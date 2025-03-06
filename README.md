# Description

The aim of this project is to predict whether an individual recently used nicotine (used within the past year) utilizing supervised learning techniques.

The dataset used includes a total of 1885 observations on 32 variables. A detailed description of the data set can be found below. Each row of the data contains observations of the following demographic and personality trait predictors:

* ID: number of record in original database. Used for reference only.
* Age: Age of the participant
* Gender: Gender of the participant (M/F)
* Education: Level of education of the participant
* Country: Country of current residence of the participant
* Ethnicity: Ethnicity of the participant
* Nscore: NEO-FFI-R Neuroticism (Ranging from 12 to 60)
* Escore: NEO-FFI-R Extraversion (Ranging from 16 to 59)
* Oscore: NEO-FFI-R Openness (Ranging from 24 to 60)
* Ascore: NEO-FFI-R Agreeableness (Ranging from 12 to 60)
* Cscore: NEO-FFI-R Conscientiousness (Ranging from 17 to 59)
* Impulsive: Impulsiveness measured by BIS-11
* SS: Sensation Seeking measured by ImpSS

Participants of the study were also questioned concerning their use of 18 legal and illegal drugs (alcohol, amphetamines, amylnitrite, benzodiazepine, cannabis, chocolate, cocaine, caffeine, crack, ecstasy, heroin, ketamine, legal highs, LSD, methadone, mushrooms, nicotine and volatile substance abuse) and one fictitious drug (Semeron) which was introduced to identify over-claimers. Usage of these drugs were measured on the class system ranging from CL0=CL6 defined below. 

* CL0 = “Never Used”
* CL1 = “Used over a decade ago”
* CL2 = “Used in last decade”
* CL3 = “Used in last year”
* CL4 = “Used in last month”
* CL5 = “Used in last week”
* CL6 = “Used in last day”.

For this project we will only use the data for nicotine use and train predictive models based on an individuals demographic and personality traits. 

# Techniques Demonstrated


### Data Processing and Feature Engineering, Decision Trees, Boosting Model, Random Forest Model with Bootstrap, Feature Importance Analysis, and Evaluation Metrics (confusion matrix, tpr, fpr)


# Data Processing and Feature Engineering

![image](https://github.com/user-attachments/assets/1faede1b-0ef5-40dd-b8f6-5fc026571def)

## Feature Engineering

![image](https://github.com/user-attachments/assets/1c5b8b89-0d07-4695-926d-f6a414b481ba)

## Data Processing and Splitting

![image](https://github.com/user-attachments/assets/fa85f204-7058-4794-9d93-eeff7bb9b07c)
![image](https://github.com/user-attachments/assets/6a59abdb-9190-413b-b90b-a91bbfdda853)

The size of our training dataset is `1000`.

The size of our testing dataset is `885`.

# Decision Tree

![image](https://github.com/user-attachments/assets/90dd35eb-4fb7-470b-88ce-0567438cc873)
![image](https://github.com/user-attachments/assets/8cce5524-20ee-4478-9931-4ccfa6f4b71a)

## Evaluation of Decision Tree

![image](https://github.com/user-attachments/assets/d01aaee8-c95b-4214-997b-91f8091eddcd)
![image](https://github.com/user-attachments/assets/4b235c10-f6ee-41f9-ad8d-5b0422a82d2f)

The TPR of the pruned single decision tree is `0.803681`.

# Boosting Model

![image](https://github.com/user-attachments/assets/a9019c1f-5b27-43f9-b684-b8c3232a87c2)

## Importance According to Boosting Model

The predictors that appear to have the most importance according to the boosting model are in order SS, Age, Impulsive, and Ascore.

# Random Forest Model

![image](https://github.com/user-attachments/assets/c834e623-29b4-47be-a665-b5b44b334dbd)

The out-of-bag estimate of error is `28.2%`. The number of variables randomly considered at each split is `3`. `500` trees were fit into the data. 

## Importance According to Random Forest Model

![image](https://github.com/user-attachments/assets/13495727-6fac-4ec0-a375-87ee0f8f9cf3)
![image](https://github.com/user-attachments/assets/66450431-412b-41fc-9805-b3ec27d631a0)

SS, Age, Impulsive, and Ascore are still important according to the random forest model, but they are not the most important. The most important predictors differs between the boosting and random forest model.

# Evaluation of Boosting Model and Random Forest Model

![image](https://github.com/user-attachments/assets/e29f2108-37ac-44a3-b8a5-749b6f018e2a)
![image](https://github.com/user-attachments/assets/00c037de-4008-4beb-94d0-90ab902f212d)
![image](https://github.com/user-attachments/assets/b6c02aa9-b806-4390-b47e-86b734f07e0e)

# Conclusion

Our boosting model True Positive Rate is `0.9836401`. This value is very high indicating that the boosting model is performing well, correctly predicting "Yes" for recent nicotine usage `98.36%` of the time. 

Our random forest model True Positive Rate is `0.9631902`. This value is also very high indicating that the random forest model is performing well, correctly predicting "Yes" for recent nicotine usage `96.32%` of the time.

Additionally the boosting and random forest model TPRs are much higher than the TPR of the pruned single decision tree.

Although TPR is an important metric for evaluating model performance, further investigating FPR would be beneficial for better understanding the performance of our models. Fitting an ROC curve and calculating the area under the curve in addition to TPR and FPR would allow us to further interpret the models accuracy when classifying nicotine use. Furthermore, in this project we set our tuning parameter for our boosting model and random forest model to `0.2` which is a lower classification threshold, increasing the models True Positive Rate, but also False Positive Rate. This increased TPR could potentially lead to a false confidence in our models performance, further emphasizing the need to investigate FPR and/or evaluate model performance with larger classification thresholds. 

Finally, an important note on the modeling of nicotine use in this project is the failure to use other drug use data. We build our model on soley demographic, personality trait, and nicotine use data of participants. We could potentially build a better model if we build more predictors based off other drug use data. For example if an individual has experimented with many drugs previously, they may be more likely to use nicotine. 



