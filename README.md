# Lung cancer visualization using Tableau

## 1. Project description

   ### Overview
This was initially my group project in the Business Analytics program. We were asked to find a dataset of any topic that we were interested in, use visualization to answer 3 questions about the topic and dataset.
     
   ### Data source
 As lung cancer is one of leading causes of death all over the world, and we have been worried about our lung health since covid-19, we wanted to understand which are the main factors causing lung cancer. We found a dataset on [Kaggle - Lung cancer prediciton](https://www.kaggle.com/datasets/thedevastator/cancer-patients-and-air-pollution-a-new-link?datasetId=2636109).

With this dataset, we will use data visualization to answer 3 questions below:
- What are the main causes of lung cancer?
- What are the main symptoms of lung cancer?
- Which is the age group that has the highest number of patients with lung cancer?

### Types of visualization

As data of all variables are categorical, except numeric variable Age, we decided to use radar and histogram chart. The radar chart is a great option that allows us to compare different categories to see the relationships and significance of each factor to the level of cancer. Besides, the histogram displays the number of patients in each age group. We used color filters to differentiate the different levels of lung cancer. And we used the tool page to see the different age groups and how the causes and symptoms increase or decrease according to the level of lung cancer.
   
## 2. Data cleaning
### Using Tableau prep tool

As the dataset was clean already, we just separate the causes and symptoms of lung cancer by renaming these factors as below:
- Causes: starting with "C-"+ field name. There are a total of 9 columns of causes being renamed:

C-Air Pollution, C-Alcohol Use, C-Dust Allergy, C-Occupational Hazards, C-Genetic Risk, C-Chronic Lung Disease, C-Obesity, C-Smoking, C-Passive Smoker

- Symptoms: starting by "S-"+ field name. There are a total of 11 columns of symptoms being renamed: 

S-Chest Pain, S-Coughing up Blood, S-Fatigue, S-Weight Loss, S-Shortness of Breath, S-Wheezing, S-Swallowing Difficulty, S-Nail Clubbing, S-Frequent Cold, S-Dry Cough, S-Snoring

### Using Tableau desktop

We pivoted columns of causes and symptoms into rows. These fields were rearranged into a new column named Causes_Symptoms and their values into Values.

Next, we created necessary fields to draw radar charts. As we wanted to separate causes and symptoms, we drew 2 radar charts:

#### Causes radar chart:

```
@angle_causes: 
RUNNING_SUM(
2*PI()/9)
+ PI()/2
@distance from center:
AVG([Values])
@x_causes:
[@distance from center]*COS([@angle_causes])
@y_causes:
[@distance from center]*SIN([@angle_causes])
```

#### Symptoms radar chart:

```
@angle_symptoms:
RUNNING_SUM(
2*PI()/11)
+ PI()/2
@distance from center:
AVG([Values])
@x_symptoms:
[@distance from center]*COS([@angle_symptoms])
@y_symptoms:
[@distance from center]*SIN([@angle_symptoms])
```

## 3. Visualization & Insights

### 1. What are the main causes of lung cancer?
![image](https://github.com/thanhhoaph/lung-cancer-visualization/assets/133604339/de399ba8-9e23-4c26-b99c-3541be25620f)
We can see that one factor remains in the top 3 in each level, dust allergy, which we might not control. For medium and low levels, we also have three other factors we might not totally control: genetic risk, occupational hazard, and chronic lung diseases like asthma, COPD, pulmonary fibrosis, asbestosis, or pneumonitis.

### 2. What are the main symptoms of lung cancer?
![image](https://github.com/thanhhoaph/lung-cancer-visualization/assets/133604339/32182b54-2109-46c3-a590-40e3cad97e68)

We can see that the most significant symptoms are chest pain, chronic lung disease, coughing blood, and fatigue. These symptoms increase significantly when the level increases. Frequent colds and shortness of breath are also symptoms that increase but not very much. And there is no such relationship for wheezing, weight loss, swallowing difficulty, and clubbing of fingernails.

### 3. Which is the age group that has the highest number of patients with lung cancer?
![image](https://github.com/thanhhoaph/lung-cancer-visualization/assets/133604339/9a9d2d1f-c0ab-41d9-8d9a-b63caa3372e2)

The 35-40 surprisingly has the most lung cancer patients. At the same time, this age group also has the most significant number of patients who have lung cancer at a high level. Meanwhile, the group 65-75, who are supposed to be more vulnerable and might have a higher chance of getting cancer, have a tiny number of patients and no one with severe levels.

To explore more about this finding, we went back to the Causes chart and found out this group had a very unhealthy lifestyle. They drink a lot, have obese, and live in a smoking environment which are the most critical causes of severe lung cancer.
![image](https://github.com/thanhhoaph/lung-cancer-visualization/assets/133604339/9206a92e-decd-49e1-b9c9-22e2ae9f8b98)
In addition, this age group's most serious symptoms include coughing up blood, chest pain, and fatigue. These symptoms show a consistent trend with the level of cancer. The higher the level of cancer is, the more severe these symptoms show. In contrast, wheezing, weight loss, and swallowing difficulty are inconsistent with the level of cancer. Therefore, more research is needed to conclude about these symptoms.
![image](https://github.com/thanhhoaph/lung-cancer-visualization/assets/133604339/4689105c-8965-49e0-904d-4c0f8769a04c)

### Key takeaway

Different factors such as smoking, alcohol use, dust allergy, obesity, genetic risk, passive smoking, and occupational hazards are the most dangerous. Some of them are undeniably like genetic risk, but many can be avoided by leading a healthier life. This project also informs various significant symptoms that might indicate lung cancer, such as coughing blood, fatigue, chest pain, shortness of breath, etc. Those who expose to these factors and have mentioned symptoms should see the doctor as soon as possible.

## 4. Team acknowledgement
Alejandra Parrilla Guzman

Irving Alejandro Covarrubias Medina

Thanh Tung Nguyen.
