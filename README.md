# Deep Color

## Overview
In this project, a CNN is created which is trained to color grayscale face images. The whole project is developed in pytorch. 

## Project Requirement
The project requirement will be found at [here](https://github.com/Shantanu48114860/Deep_Colorization/blob/master/PartII_DeepColorization.pdf).

## Requirements and versions
pytorch - 1.3.1 <br/>
numpy - 1.17.2 <br/>
pandas - 0.25.1 <br/>
scikit - 0.21.3 <br/>
matplotlib - 3.1.1 <br/>
python -  3.7.4 <br/>


## Dependencies
[python 3.7.7](https://www.python.org/downloads/release/python-374/)

[pytorch 1.3.1](https://pytorch.org/get-started/previous-versions/)

## Dataset
The dataset will be found at [here](https://github.com/Shantanu48114860/Deep_Colorization/tree/master/DeepColor/face_images).

## Program Execution

```shell
python main.py
```



## Folder Structure

```tex
DeepColor
   ├── Colorize_deep.py
   ├── Colorizer.py
   ├── Colorizer_Manager.py
   ├── Constants.py
   ├── Regressor.py
   ├── Regressor_Manager.py
   ├── buildDataset.py
   ├── utils.py
   ├── main.py
   ├── README.md
   ├── Model
   │   ├── Colorizer
   │   └── Regressor
   ├── Plots
   │   ├── Colorizer
   │   ├── Final
   │   └── Regressor
   ├── __pycache__
   ├── data
   │   ├── test
   │   └── train
   ├── face_images
   ├── outputs_sigmoid
   │   ├── color
   │   └── gray
   └── outputs_tanh
       ├── color
       └── gray
```



## Architecture

The Colorizer Network is defined in `Colorizer.py` which internally invokes the Regressor model written in `Regressor.py`, responsible for extracting the features from the batch of images.

`ColorizerManager.py` has the `train` and `test` method which is responsible to training and testing the models from the respective ***train*** and ***test*** datasets provided. 

First, it receives the data in the defined `batch-size` from the `DataLoader` , retreives the hyperparameters from `Constants.py` and then trains the networks for the given number of epochs.

Once the network is trained, we ***test*** the model by loading the test data and subsequently store the outputs under the `outputs_sigmoid` and `outputs_tanh` folders for the respective runs as per requirement.



For the Regressor, there is a separate `Regressor_Manager.py` that trains and tests the model to generate the required performance and plots the ***Loss function*** over the epochs. The plot of the same is stored under `Plots->Regressor` .



## Outputs

1. #### Regressor

   The regressor outputs two scalar values which are the average of the `a` and `b` channel for each of the images.

2. #### Colorizer

   The colorizer output color images and stores the same in the respective `output` folder based on the activation function. The grayscale images are stored under the **gray** folder and the colorized images goes into the **color** folder.

   

## GPU

The code extracts the `device` at the start of execution using ` torch.cuda.is_available()` and loads the tensors accordingly, leveraging the compute based on availability.



## Hyperparameters

The following hyperparameters have been considered:

- Learning Rate
- Weight Decay
- Number of Epochs

These have been defined inside the `Utils` class under `get_hyperparameters()` .  The parameters are defined as a dictionary and the function returns a list having the list of parameters respectively. Following this, during runtime, using `itertools.product` to generate a cartesian product of the list of hyperparameters, the training has been done for each set of hyperparameters. 

## Generated output with Sigmoid activation function
For every triplet, from left to right are gray scale, original and colored reconstructed images <br/>
<img src="https://github.com/Shantanu48114860/Deep_Colorization/blob/master/Report_Supplementary/Sigmoid.jpg">

## Generated output with Tanh activation function
For every triplet, from left to right are gray scale, original and colored reconstructed images <br/>
<img src="https://github.com/Shantanu48114860/Deep_Colorization/blob/master/Report_Supplementary/tanh.jpg">

## Project Report
The detailed report will be found at [here](https://github.com/Shantanu48114860/Deep_Colorization/blob/master/Report.pdf).


## Contributors

- [Kalpak Seal](https://github.com/kalpak92)
- [Shantanu Ghosh](https://github.com/Shantanu48114860)

