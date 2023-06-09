# Finger Flexion Prediction using LightGBM + GridSearchCV

![](https://github.com/toastedqu/be521-bci-comp/blob/main/workflow.png)

Collaborators: Tegan Thurston, Nidhi Bali

We participated in the BCI Competition IV: ECoG to Finger Movements via BE521 (Brain-Computer Interface) by Prof. Brian Litt.

Given ECoG signals and finger flexion data of 3 subject, build a model to predict their finger movements using a limited subset of the original data.

Our algorithm consists of 3 main parts: feature engineering, model prediction, and output upsampling. The following steps are performed on each subject independently. First, we filter the data to get rid of unnecessary noises. We extract 5 window features from the filtered data: line length, energy, bandpowers between 75-115, 125-159, and 159-175 Hz, and we normalize the features using the standard scalers obtained from the training process. Second, we use the trained LightGBM models to predict the flexion of each finger and concatenate the results of all the 5 fingers. Lastly, we upsample the predictions using CubicSpline interpolation and use the upsampled results as the final output. Figure 1 illustrates the entire pipeline.
