# PoseTReID and Dataset

## 🖇 PoseTReID

<div align="center">

<img src="https://raw.githubusercontent.com/rathaumons/PoseTReID_DATASET/master/PoseTReID.png">

</div>

***PoseTReID*** is a generic framework which combines detector, tracker, and re-identifier in order to effectively track specific people accross multiple cameras or video scenses, in both short and long term for distributed contexts of people interaction spaces such as malls or amusement parks, etc. Check more our paper for more details -> [[IEEE]](https://ieeexplore.ieee.org/document/9271712).

## 🖴 Dataset #1: `GTA_V_DATASET`

<div align="center">

<img src="https://raw.githubusercontent.com/rathaumons/PoseTReID_DATASET/master/overview.png">

</div>

`GTA_V_DATASET` dataset is specifically designed for testing our ***PoseTReID*** in our distributed contexts. All videos were rendered in 16:9 ratio at a resolution of 1080p with our custom script. Afterwards, they were down-scaled to 720p to fit our real-time testing scenarios and to be more realistic like real-life cameras. 

The ground-truth is provided in 2 different formats such as `.txt` and `.csv` for every video with the real IDs (names) of the characters.

This dataset is shared under license: [Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)](https://creativecommons.org/licenses/by-sa/4.0/legalcode).

<img src="https://raw.githubusercontent.com/rathaumons/PoseTReID_DATASET/master/cc-by-sa.png" width="128">

### 🆕 Updated 2023:

The new ground-truth consists of bouding boxes of `[x y width height]` and `[x1 y1 x2 y2]`, semi-generated by [`pyppbox`](https://github.com/rathaumons/pyppbox) V3 using the following modules:
  - Detector = YOLO Ultralytics V8 (`yolov8l.pt`, `conf=0.5`, `iou=0.7`, `imgsz=416`)
  - Tracker = SORT
  - ReIDer = DeepReID (OSNet-AIN) + Custom

Each line in the ground-truth text file represents a person in a frame, and it contains info separated by `\t` as following:

`Frame index` `\t` `Represent point (x, y)` `\t` `Name ID` `\t` `Box [x y width height]` `\t` `Box [x1 y1 x2 y2]`

```
...
187	(881, 307)	Trevor	[826 242 110 260]	[826 242 936 502]
188	(233, 367)	Michael	[ 9 253 448 456]	[ 9 253 457 709]
188	(639, 304)	Franklin	[586 240 107 258]	[586 240 693 498]
188	(881, 307)	Trevor	[826 242 110 260]	[826 242 936 502]
189	(221, 354)	Michael	[16 236 410 472]	[16 236 426 708]
189	(639, 304)	Franklin	[586 240 107 259]	[586 240 693 499]
189	(881, 307)	Trevor	[826 242 110 260]	[826 242 936 502]
...
```

### 🆕 `pyppbox-data-gta5`:

[`pyppbox-data-gta5`](pyppbox-data-gta5) is a package of the restructured `GTA_V_DATASET` for [`pyppbox`](https://github.com/rathaumons/pyppbox) V3.

Download from [releases](https://github.com/rathaumons/PoseTReID_DATASET/releases) or install directly:
```
pip install https://github.com/rathaumons/PoseTReID_DATASET/releases/download/v2.0/pyppbox_data_gta5-2.0-py3-none-any.whl
```

[![Build](https://github.com/rathaumons/PoseTReID_DATASET/actions/workflows/build.yaml/badge.svg)](https://github.com/rathaumons/PoseTReID_DATASET/actions/workflows/build.yaml)

## 🚀 Code?

For result and evaluation tools, please check our [`pyppbox`](https://github.com/rathaumons/pyppbox).

## 🔗 Papper Citation
Please kindly cite this paper if you use this dataset in your paper [[IEEE]]([***PoseTReID***](https://ieeexplore.ieee.org/document/9271712)):
```
@INPROCEEDINGS{ptreid9271712,
  author={Siv, Ratha and Mancas, Matei and Sreng, Sokchenda and Chhun, Sophea and Gosselin, Bernard},
  booktitle={2020 12th International Conference on Information Technology and Electrical Engineering (ICITEE)}, 
  title={People Tracking and Re-Identifying in Distributed Contexts: PoseTReID Framework and Dataset}, 
  year={2020},
  pages={323-328},
  doi={10.1109/ICITEE49829.2020.9271712}}
```
