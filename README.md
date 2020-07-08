### Compilation Memo which I use, may work or may not.
1. Use Win10 + VS2017
2. Steam GTAV lastest (202007)
3. Need capture.hk server.hk gta5.hk (together with gamehook.dll & scripthookv.dll), use python.hk later
4. Comment line in wrapper/dx11.cpp, in case GTAV crashes.
5. http://localhost:8766/targets see all targets
6. http://localhost:8766/settings?fps=1&W=1280&H=720&targets=texture_id  then view results in http://localhost:8766/view
7. all results in GTA game folder cap/xxxx
8. compile python.hk: python -> properties -> VC++ Directories -> includes/reference directory -> set python headers and libs (C:\Program Files (x86)\Microsoft Visual Studio\Shared\Python37_64\include)
9. 

## Does computer vision matter for action?

[Brady Zhou](http://www.bradyzhou.com), [Philipp Krähenbühl](http://www.philkr.net), and [Vladlen Koltun](http://www.vladlen.info)  
Science Robotics, 4(30), 2019  
[Paper](https://robotics.sciencemag.org/content/4/30/eaaw6661?ijkey=z3zMGrf4SfjN6&keytype=ref&siteid=robotics)  
[Project](http://www.bradyzhou.com/visionforaction/)

Code to accompany the paper.  

<img src="logo.jpg" style="width: 300px;"/>

## Installation

```
git clone --recursive https://github.com/intel-isl/vision-for-action.git
```

#### ViZDoom

We require building from source using the included submodule,  
which includes hacks for getting labels for the walls and floors.

```bash
cd ViZDoom
cmake -DCMAKE_BUILD_TYPE=Release -DBUILD_PYTHON3=ON
make
```

Link ViZDoom and helpers to `PYTHONPATH`.

```bash
export PYTHONPATH=$PYTHONPATH:$PWD/ViZDoom/bin/python3.6/pip_package
export PYTHONPATH=$PYTHONPATH:$PWD
```

#### GTA V

This is supported on Windows machines only, and will take a little bit of effort.

You will need to install the following -

- a modified [GameHook](https://github.com/bradyz/gamehook)
- a modified [GameHook GTA V Plugin](https://github.com/bradyz/gamehook_gtav)
- a modified [PyHookV](https://github.com/bradyz/pyhookv)

After successfully building all of these projects, you should have

```
dxgi.dll (renamed from gamehook.dll)
python.hk
server.hk
gta5.hk
pyhookv.pyd
```

Take all of these files and put them in the directory where `GTAV.exe` lives.  
Additionally, move the following files from the `gta_v` directory to the same directory.

```
agents_privileged.py
constants.py
controller.py
controls.py
message_packer.py
pyhookv_utils.py
presets.py
scenarios.py
```

## Citation

```
@article{Zhou2019DoesCV,
  title={Does computer vision matter for action?},
  author={Brady Zhou and Philipp Kr{\"a}henb{\"u}hl and Vladlen Koltun},
  journal={Science Robotics},
  volume={4},
  number={30},
  year={2019}
}
```
