## GAN Colorizer

Using a generative adversarial network to "hallucinate" color in black and white photos.

Work in progress.



Generator summary...

____________________________________________________________________________________________________
Layer (type)                     Output Shape          Param #     Connected to
====================================================================================================
input_1 (InputLayer)             (None, 32, 32, 3)     0
____________________________________________________________________________________________________
conv2d_1 (Conv2D)                (None, 32, 32, 32)    896         input_1[0][0]
____________________________________________________________________________________________________
activation_1 (Activation)        (None, 32, 32, 32)    0           conv2d_1[0][0]
____________________________________________________________________________________________________
conv2d_2 (Conv2D)                (None, 32, 32, 32)    9248        activation_1[0][0]
____________________________________________________________________________________________________
activation_2 (Activation)        (None, 32, 32, 32)    0           conv2d_2[0][0]
____________________________________________________________________________________________________
batch_normalization_1 (BatchNorm (None, 32, 32, 32)    128         activation_2[0][0]
____________________________________________________________________________________________________
max_pooling2d_1 (MaxPooling2D)   (None, 16, 16, 32)    0           batch_normalization_1[0][0]
____________________________________________________________________________________________________
conv2d_3 (Conv2D)                (None, 16, 16, 64)    18496       max_pooling2d_1[0][0]
____________________________________________________________________________________________________
activation_3 (Activation)        (None, 16, 16, 64)    0           conv2d_3[0][0]
____________________________________________________________________________________________________
conv2d_4 (Conv2D)                (None, 16, 16, 64)    36928       activation_3[0][0]
____________________________________________________________________________________________________
activation_4 (Activation)        (None, 16, 16, 64)    0           conv2d_4[0][0]
____________________________________________________________________________________________________
batch_normalization_2 (BatchNorm (None, 16, 16, 64)    256         activation_4[0][0]
____________________________________________________________________________________________________
max_pooling2d_2 (MaxPooling2D)   (None, 8, 8, 64)      0           batch_normalization_2[0][0]
____________________________________________________________________________________________________
conv2d_5 (Conv2D)                (None, 8, 8, 128)     73856       max_pooling2d_2[0][0]
____________________________________________________________________________________________________
activation_5 (Activation)        (None, 8, 8, 128)     0           conv2d_5[0][0]
____________________________________________________________________________________________________
batch_normalization_3 (BatchNorm (None, 8, 8, 128)     512         activation_5[0][0]
____________________________________________________________________________________________________
up_sampling2d_1 (UpSampling2D)   (None, 16, 16, 128)   0           batch_normalization_3[0][0]
____________________________________________________________________________________________________
conv2d_6 (Conv2D)                (None, 16, 16, 128)   147584      up_sampling2d_1[0][0]
____________________________________________________________________________________________________
activation_6 (Activation)        (None, 16, 16, 128)   0           conv2d_6[0][0]
____________________________________________________________________________________________________
batch_normalization_4 (BatchNorm (None, 16, 16, 128)   512         activation_6[0][0]
____________________________________________________________________________________________________
up_sampling2d_2 (UpSampling2D)   (None, 32, 32, 128)   0           batch_normalization_4[0][0]
____________________________________________________________________________________________________
conv2d_7 (Conv2D)                (None, 32, 32, 64)    73792       up_sampling2d_2[0][0]
____________________________________________________________________________________________________
activation_7 (Activation)        (None, 32, 32, 64)    0           conv2d_7[0][0]
____________________________________________________________________________________________________
batch_normalization_5 (BatchNorm (None, 32, 32, 64)    256         activation_7[0][0]
____________________________________________________________________________________________________
merge_1 (Merge)                  (None, 32, 32, 67)    0           batch_normalization_5[0][0]
                                                                   input_1[0][0]
____________________________________________________________________________________________________
conv2d_8 (Conv2D)                (None, 32, 32, 32)    19328       merge_1[0][0]
____________________________________________________________________________________________________
activation_8 (Activation)        (None, 32, 32, 32)    0           conv2d_8[0][0]
____________________________________________________________________________________________________
conv2d_9 (Conv2D)                (None, 32, 32, 3)     867         activation_8[0][0]
____________________________________________________________________________________________________
activation_9 (Activation)        (None, 32, 32, 3)     0           conv2d_9[0][0]
====================================================================================================
Total params: 382,659
Trainable params: 381,827
Non-trainable params: 832
____________________________________________________________________________________________________

Discriminator summary...

_________________________________________________________________
Layer (type)                 Output Shape              Param #
=================================================================
input_2 (InputLayer)         (None, 32, 32, 3)         0
_________________________________________________________________
conv2d_10 (Conv2D)           (None, 32, 32, 64)        1792
_________________________________________________________________
activation_10 (Activation)   (None, 32, 32, 64)        0
_________________________________________________________________
average_pooling2d_1 (Average (None, 16, 16, 64)        0
_________________________________________________________________
conv2d_11 (Conv2D)           (None, 16, 16, 64)        36928
_________________________________________________________________
activation_11 (Activation)   (None, 16, 16, 64)        0
_________________________________________________________________
conv2d_12 (Conv2D)           (None, 16, 16, 128)       73856
_________________________________________________________________
activation_12 (Activation)   (None, 16, 16, 128)       0
_________________________________________________________________
average_pooling2d_2 (Average (None, 8, 8, 128)         0
_________________________________________________________________
dropout_1 (Dropout)          (None, 8, 8, 128)         0
_________________________________________________________________
flatten_1 (Flatten)          (None, 8192)              0
_________________________________________________________________
dense_1 (Dense)              (None, 256)               2097408
_________________________________________________________________
activation_13 (Activation)   (None, 256)               0
_________________________________________________________________
dropout_2 (Dropout)          (None, 256)               0
_________________________________________________________________
dense_2 (Dense)              (None, 2)                 514
_________________________________________________________________
activation_14 (Activation)   (None, 2)                 0
=================================================================
Total params: 2,210,498
Trainable params: 2,210,498
Non-trainable params: 0
_________________________________________________________________


GAN summary...
_________________________________________________________________
Layer (type)                 Output Shape              Param #
=================================================================
input_3 (InputLayer)         (None, 32, 32, 3)         0
_________________________________________________________________
model_1 (Model)              (None, 32, 32, 3)         382659
_________________________________________________________________
model_2 (Model)              (None, 2)                 2210498
=================================================================
Total params: 2,593,157
Trainable params: 2,592,325
Non-trainable params: 832
_________________________________________________________________
