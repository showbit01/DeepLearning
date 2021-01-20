## Task : Transfer Learning using Fine-Tunning
Fine-tune the VGG model (you may choose what layers to fine-tune) for one category from the PASCAL dataset, and evaluate the one-versus-rest binary classification performance. Please fill your preferences in the following sheet:  https://docs.google.com/spreadsheets/d/1E76joEv1Ph7ku7VKWPpfnXqDHMvO_H4C-ftd-UMhthU/edit?usp=sharing 


### Model Used: VGG 16 with input (128,128,3)
### Data Set Used: Pascal VOC 2012
### Pre-Processing: 
* Images: 
   * Images Path: /VOC2012/JPEGImages/*
   * Each image converted to array form and then normalized to bring in the range of 0 to 1.
   * Image Size: 128*128*3
   * Images name and image generated array are appended at a single time to keep the track of which image belongs to which filename.
* Labels :
   * Labels Path : /VOC2012/ImageSets/Main/*_trainval.txt
   * Each text file contains +1 and -1 values against the image ID and the class name is the label of the text file.
   * From this Main folder, classes and image labels are extracted.
* Dataset Preparation : 
   * Image labels and array value against the name of the file  are clubbed together and then saved for the future purpose to avoid re-processing of the above steps
* Model FineTunning and classification:
   * Load the model with trained weights of ImageNet dataset
   * Remove the last layer of the model(Classification or prediction layer)
   * Set all the layers as non-trainable
   * Add a dense layer with 20 neurons, it resembles our 20 class classification
   * Now, training the model with the splitting of 80-20 for train and test data respectively
   * Test the models for the test set and analyze the predictions
   * We have selected bus as our class to classify but unfortunately, our model probably gets overfit thus giving predictions for on person class.
   * Metrics used :accuracy, Loss Function Used: binary_crossentropy(training)
   * Loss Function used for model layers : Relu other and softmax for last dense layer
