MY REPORT

Dataset Exploration
===================

Data Summary
------------

Downloaded dataset from : https://d17h27t6h515a5.cloudfront.net/topher/2017/February/5898cd6f_traffic-signs-data/traffic-signs-data.zip

1. Dataset has train, test and validataion samples samples coverting 43 classes (traffic sign classes)
    - Number of train samples = 34799
    - Number of test samples = 12630
    - Number of validation sample = 4410
2. Each train sample is of size 32 x 32 and depth of 3
   - Each sample is converted to gray scale
   - Each sample is normalized to (pixel_value - 128)/128
   
Exploratory Visualization
-------------------------

Data visualization shown in "Traffic_Sign_Classifier.ipynb"


Design and Test a Model Architechture
=====================================


Preprocessing
-------------

The submission describes the preprocessing techniques used and why these techniques were chosen.

<Ans> 
    1. MNIST data trained using LeNet is of gray images. Also, the color is not the feature that is used in 
      LeNet classification of MNIST. Based on the same assumption/concept. I used gray images as input train dataset
      Also, normalized such that pixels values are in the range of [-1, 1]. As, curves/edges are the real features from 
      which the network learns. Best way to represent edges/curves intensity is with normalized pixel values
    2. Also, by normalizing the date the mean will be zero and have equal variance 
 
 Used train and test split from sklearn (80% train, 20% test)
 Model Architecture
 ------------------
 
 The model architecture used in LeNet and below are the details of it
 
 Input image: 32 x 32 x 1 
 
                              IP          Filter Size  FeatureMap/Depth   Stride  Padding        OP
 Layer1:     
 
              Conv1      32 x 32 x 1         5 x 5           6             1       0        28 x 28 x 6
              ReLU       28 x 28 x 6                                                        28 x 28 x 6              
              MaxPool    28 x 28 x 6         2 x 2                         2       0        14 x 14 x 6
 Layer2:      
 
              Conv2      14 x 14 x 6         5 x 5          16             1       0        10 x 10 x 16
              ReLu       10 x 10 x 16                                                       10 x 10 x 16
              MaxPool    10 x 10 x 16        2 x 2                         2       0         5 x 5 x 16
 Layer3:      
              
              Conv3       5 x  5 x 16        5 x 5          400            1       0         1 x 1 x 400
              ReLu        1 x  1 x 400                                                       1 x 1 x 400
 
 fc1    :     Layer 2 o/p - 5 x 5 x 16   -> output 400
 
 fc2    :     Layer 3 0/p - 1 x 1 x 400  -> output 400
 
 Output :     FC             800                                                                 43
 
 Model Training
 --------------
 
 Hyper parameters
 ---------------
 EPOCH = 50
 LEARNING RATE = 0.0009
 Mean(Mu) = 0, Stddev(Sigma) = 0.1  (For weight distribution/initialization)
  Dropout = 0.5 (Training)
 
 Others:
 -------
 Activation Function: ReLu
 Optimizer:  Adam
 Loss: CrossEntropy
 Probability of Classification: Softmax
 
 Solution Approach:
 -------------------
 Used predefined LeNet architecture. 
 Tweaking hyper parameters using trial and error method.
 Changing train and test spilt percentage 
 Using different kernel sizes, feature maps in each layer
 Trying with different dropout factor 
 
 Training accuracy: 99.3%
 Test Accuracy: 94.6%
 
 Acquiring New Images:
 ---------------------
 Downloaded from google, samples are in "myimages" project folder
 
 Performance on New Images:
 ---------------------------
 Taken 5 new images of different classes, and classification is 100% 
 
 Model Certanity- Softmax Probabilities:
 --------------------------------------
 Ploted in "Traffic_Sign_Classifier.ipynb"
 
 
 
 
 
 
 
 
    
 


