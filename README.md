# Automated Labeling System on Film Clips of Head Detection and Localization

### Author: Zilei Shao

This project aims to create an automated feature labeling system for film clips, with a focus on head detection and localization. The main model to use as a starting point is YOLOv5s, which has been pre-trained using COCO dataset.

The folder "yolov5" is from open source of YOLOv5 algorithm. And the folder "datasets" contains COCO128 dataset and Hollywood Heads Dataset.

The two models trained with Dataset 1 and Dataset 2 can be found under the folder "yolov5," named as "Model1.pt" and "Model2.pt". The dataset used to training can be found following the path: ..\datasets\HollywoodHeads\Training and ..\datasets\HollywoodHeads\Training1. The test data is in the folder "HollywoodHeads," too.

And to add your own dataset for training and testing, please refer to the file "format_converting.ipynb." With running this file, you can convert the XML files of annotations for images to TXT files that are compatible with the format YOLOv5 requires.

The film clips used to detect heads are in the folder "..\yolov5\detect_data".

The detecting results mentioned in the final report can be found following the path: ..\yolov5\runs\detect\, and the summary of detecting results is in the file "Results of detection.xlsx". The training results can be found along the path: ..\yolov5\runs\train

Next, I will introduce the commands used to train and use the model using YOLOv5s.pt as the starting point.

1. Training

This command requires a configuration file specifying the path to training data and testing data, as well as the class number and names. We need to create a yaml file before training.

Other parameters can be changed as we want to adjust the process of training.

    $ python train.py --img 640 --batch 16 --epochs 10 --data data1.yaml --weights yolov5s.pt

2. Detecting

This command requires the path to the file needed detecting. The file can be a mp4 file, a JPG/PNG image file, or a folder contains multiple image/mp4 files.

    $ python detect.py --source path-to-file --weights Model1.pt