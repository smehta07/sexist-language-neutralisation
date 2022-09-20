# Sexist Language Neutralisation

This project is about using machine learning to automatically neutralise sexist language. This project builds upon the work by Pryzant et. al (2019), who created the first generative model to automatically neutralise subjective bias in textual data. This repository contains all of the code used in this project. We fine-tuned this model using the "Call Me Sexist" dataset (Samory et al., 2021), consisting of 2,405 sexist tweets and their neutralised pairs. For example, if we have the following sexist sentence: "women are more likely than men to act in silly ways", the model could neutralise this into "some individuals are more likely to act in silly ways". We used two new automatic evaluation methods for this model: sentence embeddings and the use of a sexism classification model. In addition, we propose an automated training data augmentation pipeline to improve our model further. For more detail on this project, please see the Report.pdf file. 

The repository is structured as follows:
- The current directory contains two python notebooks that can be run using Google Colab. The "NLP_Model" notebook contains the code to pre-process the data, fine tune the model, run inference and evaluate our models. The "Demo" notebook is a shorter version of the other notebook which can be used to demonstrate our code. Please reach out if you would like to run the demo code as model checkpoints can be provided. 
- The neutralizing-bias folder contains the code for the pre-trained model created by Pryzant et. al (2019). The paper for this code can be found here: https://arxiv.org/pdf/1911.09709.pdf. This repository was used to fine tune and run inference on the models. We made some changes to the following files to work with our dataset: 
    - harvest/gen_data_from_crawl.py 
    - harvest/add_tags.py 
    - src/shared/data.py
- The data folder contains the raw and processed data for the models. This is broken up into train, test, augmented_data and human_eval folders. The train and test folders were used to fine tune the pre-trained model baseline, the augmented data was used to train a second fine tuned model and the human_eval data was used for manually evaluating the results of the baseline, fine tuned, and augmented data models. 
- The baseline_model folder contains the results of running inference on the baseline model created by Pryzant et. al (2019). 
- The fine_tuned_model folder contains the results of fine tuning the baseline model on the Call Me Sexist dataset. 
- The augmented_data_model folder contains of the second iteration of fine tuning the fine tuned model on another sexist dataset (in train1, train2 and train3). This second dataset is the Workplace Sexism Dataset introduced by Grosz et. al (2020). The results of running inference on a test set from another sexist dataset is in the test folder. 
- The demo folder is used for the interactive part of the demo (see Demo.ipynb for more details)

References: 
1. Reid Pryzant, Richard Diehl Martinez, Nathan Dass, Sadao Kurohashi, Dan Jurafsky, and Diyi Yang. 2020. Automatically neutralizing subjective bias in text. In AAAI. https://arxiv.org/pdf/1911.09709.pdf
2. Mattia Samory, Indira Sen, Julian Kohne, Fabian Flöck, and Claudia Wagner. 2021. "call me sexist, but..." : Revisiting sexism detection using psychological scales and adversarial samples. In ICWSM. https://arxiv.org/pdf/2004.12764v2.pdf
3. Dylan Grosz and Patricia Conde-Cespedes. 2020. Automatic detection of sexist statements commonly used at the workplace. In Pacific-Asia Conference on Knowledge Discovery and Data Mining, pages 104– 115. Springer. https://arxiv.org/abs/2007.04181 