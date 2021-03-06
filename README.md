# Depixelizer
<a href="https://colab.research.google.com/drive/1pRAMgGV6cXPMflYHc8OQwbhLv4XQYrwk?usp=sharing"><img src="https://camo.githubusercontent.com/84f0493939e0c4de4e6dbe113251b4bfb5353e57134ffd9fcab6b8714514d4d1/68747470733a2f2f636f6c61622e72657365617263682e676f6f676c652e636f6d2f6173736574732f636f6c61622d62616467652e737667">
</a>

<img height="50%" width="50%" src="https://i2.wp.com/sefiks.com/wp-content/uploads/2018/03/convolutional-autoencoder.png?fit=1818%2C608&ssl=1">

AI model to remove pixel noise from text images. 

## Description

Depixelizer is a Convolutional AutoEncoder model. The goal is to learn a function to reconstruct "pixeled" text images. 

To train the model I generate two kind of text images, clean and pixeled. The clean image is a text image with a white background and black text, the corresponding pixeled image is the same image with pixel noise. You can download the dataset from this directory or use your own dataset. You can also generate a new dataset from the Colab notebook using the script. 

In my experiments I generate images using only one font (Roboto), but to improve the model generalization ability you can use multiple fonts.

| **Input** (x)  |  **Desired output** (y) |
|----|---|
| <img src="https://github.com/samirsalman/Depixelizer/blob/main/examples/pixeled.png"> |  <img src="https://github.com/samirsalman/Depixelizer/blob/main/examples/clean.png"> |

## Dataset Structure

- **dataset**
  - **clean**
    - 20.000 clean images (each image name is <ID.png>)   
  - **pixeled**  
    - 20.000 pixeled images (each image name is <ID.png>) 

## Convoutional AutoEncoder Model
```=================================================================
Layer (type:depth-idx)                   Param #
=================================================================
AutoEncoder                              --
├─Sequential: 1-1                        --
│    └─Conv2d: 2-1                       168
│    └─ReLU: 2-2                         --
│    └─MaxPool2d: 2-3                    --
│    └─Conv2d: 2-4                       660
│    └─ReLU: 2-5                         --
│    └─MaxPool2d: 2-6                    --
│    └─Conv2d: 2-7                       2,616
│    └─ReLU: 2-8                         --
│    └─MaxPool2d: 2-9                    --
├─Sequential: 1-2                        --
│    └─ConvTranspose2d: 2-10             1,164
│    └─ReLU: 2-11                        --
│    └─ConvTranspose2d: 2-12             294
│    └─ReLU: 2-13                        --
│    └─ConvTranspose2d: 2-14             75
├─MSELoss: 1-3                           --
=================================================================
Total params: 4,977
Trainable params: 4,977
Non-trainable params: 0
=================================================================
```

## Model prediction examples

<img src="https://github.com/samirsalman/Depixelizer/blob/main/examples/preds4.png">


## Todo

- [ ] Improve predictions quality
- [ ] Data augmentation
- [ ] Use more fonts to generate the dataset


## Authors

Samir Salman
