# EX-05-Feature-Generation


## AIM
To read the given data and perform Feature Generation process and save the data to a file. 

# Explanation
Feature Generation (also known as feature construction, feature extraction or feature engineering) is the process of transforming features into new features that better relate to the target.
 

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature Generation techniques to all the feature of the data set
### STEP 4
Save the data to the file


# CODE
```
Program Developed:R.K PRAGALYAA SHREE
Register number:212221040125
```

## Data.csv
```
import pandas as pd
df=pd.read_csv("data.csv")
df

from sklearn.preprocessing import LabelEncoder, OrdinalEncoder
from sklearn.preprocessing import OneHotEncoder

oe=OrdinalEncoder()
df1=df.copy()

df1["City"] = oe.fit_transform(df1[["City"]])
df1["bin_1"] = oe.fit_transform(df1[["bin_1"]])
df1["Ord_1"] = oe.fit_transform(df1[["Ord_1"]])
df1["Ord_2"] = oe.fit_transform(df1[["Ord_2"]])
df1["bin_2"] = oe.fit_transform(df1[["bin_2"]])

df2=df.copy()

#feature scaling
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
df2=pd.DataFrame(sc.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df2

from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
df3=pd.DataFrame(sc1.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df3

from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
df4=pd.DataFrame(sc2.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df4

from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
df5=pd.DataFrame(sc3.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df5
```
## Encoding.csv
```
import pandas as pd
qf=pd.read_csv("encoding.csv")
qf

from sklearn.preprocessing import LabelEncoder, OrdinalEncoder
from sklearn.preprocessing import OneHotEncoder

oe=OrdinalEncoder()

qf1=qf.copy()


qf1["bin_1"] = oe.fit_transform(qf1[["bin_1"]])
qf1["nom_0"] = oe.fit_transform(qf1[["nom_0"]])
qf1["ord_2"] = oe.fit_transform(qf1[["ord_2"]])
qf1["bin_2"] = oe.fit_transform(qf1[["bin_2"]])

#feature scaling
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
qf0=pd.DataFrame(sc.fit_transform(qf1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
qf0   

from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
qf2=pd.DataFrame(sc1.fit_transform(qf1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
qf2

from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
qf3=pd.DataFrame(sc2.fit_transform(qf1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
qf3

from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
qf4=pd.DataFrame(sc3.fit_transform(qf1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
qf4
```
## Titanic_dataset.csv
```
import pandas as pd
rf=pd.read_csv("titanic.csv")
rf

#removing unwanted data
rf.drop("Name",axis=1,inplace=True)
rf.drop("Ticket",axis=1,inplace=True)
rf.drop("Cabin",axis=1,inplace=True)  

rf["Age"]=rf["Age"].fillna(rf["Age"].median())
rf["Embarked"]=rf["Embarked"].fillna(rf["Embarked"].mode()[0])

rf.isnull().sum()

rf1=rf.copy()

from sklearn.preprocessing import LabelEncoder, OrdinalEncoder
embark=['S','C','Q']
oe=OrdinalEncoder()

e1=OrdinalEncoder(categories=[embark])
rf1['Embarked'] = e1.fit_transform(rf[['Embarked']])
rf1['Sex'] = oe.fit_transform(rf[['Sex']])
rf1

#feature scaling
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
rf0=pd.DataFrame(sc.fit_transform(rf1),columns=['PassengerId', 'Survived', 'Pclass', 'Sex','Age','SibSp','Parch','Fare','Embarked'])
rf0

from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
rf3=pd.DataFrame(sc1.fit_transform(rf1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
rf3

from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
rf4=pd.DataFrame(sc2.fit_transform(rf1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
rf4

from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
rf5=pd.DataFrame(sc3.fit_transform(rf1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
rf5
```

## OUPUT
## Data.csv:
## Initial dataset:
![00001](https://user-images.githubusercontent.com/128135934/233819724-e9064e32-e948-401b-b8f1-0fe5b06f49b9.png)

## Encoded dataset:
![0002](https://user-images.githubusercontent.com/128135934/233819802-86164088-cad7-4bc8-bf5e-15c628c623a0.png)

## Data scaling using MinMaxScaler:
![0003](https://user-images.githubusercontent.com/128135934/233819818-c97937c3-ce2b-4a92-baa1-7e4fa6eda7f2.png)

## Data scaling using StandardScalar:
![0004](https://user-images.githubusercontent.com/128135934/233819833-18d4ee9d-a1a2-4db6-94e8-6431ed137f70.png)

## Data scaling using MaxAbsScaler:
![0005](https://user-images.githubusercontent.com/128135934/233819859-ff130464-2b8f-41ff-a3db-4e272c439e21.png)

## Data scaling using RobustScaler:
![0006](https://user-images.githubusercontent.com/128135934/233819878-7e7b1f3a-c318-4096-945b-7c37e70a0462.png)

## Encoding.csv:
## Initial dataset:
![0007](https://user-images.githubusercontent.com/128135934/233819899-5dcac63d-ea25-4bce-8df0-95942eada52f.png)

## Encoded dataset:
![0008](https://user-images.githubusercontent.com/128135934/233819919-74baeb37-e508-4ad2-8ced-42dac4a0e555.png)

## Data scaling using MinMaxScaler:
![0009](https://user-images.githubusercontent.com/128135934/233819932-71d53619-b038-4d09-a8ce-2e8ba6ebaa07.png)

## Data scaling using StandardScalar:
![pra](https://user-images.githubusercontent.com/128135934/233819947-f75181b7-80bc-44b6-978d-651477a502ba.png)

## Data scaling using MaxAbsScaler:
![gal](https://user-images.githubusercontent.com/128135934/233819969-ac683664-fe70-472d-be6e-d210696998cf.png)

## Data scaling using RobustScaler:
![yaa](https://user-images.githubusercontent.com/128135934/233819997-b9a943a3-4cc1-45f3-86cf-fc38ebb81cd1.png)

## Titanic_dataset.csv:
## Initial dataset:
![s](https://user-images.githubusercontent.com/128135934/233820016-80f420d5-6983-459d-94c1-fd6029e34bc2.png)

## isnull.sum()
![h](https://user-images.githubusercontent.com/128135934/233820042-7e779249-f8a1-4cd7-926b-0f55c1bfad61.png)

## Encoded dataset:
![r](https://user-images.githubusercontent.com/128135934/233820060-d9b25ae8-ea67-4a38-9398-529b3a04b94a.png)

## Data scaling using MinMaxScaler:
![e](https://user-images.githubusercontent.com/128135934/233820088-a6cdf52c-efb3-4214-bb00-6c004410f485.png)

## Data scaling using StandardScalar:
![do](https://user-images.githubusercontent.com/128135934/233820103-2252847b-11ee-4330-9bd5-8b4e171930cb.png)

## Data scaling using MaxAbsScaler:
![re](https://user-images.githubusercontent.com/128135934/233820119-e361bf35-f6e0-44c8-9d0a-82a05996e969.png)

## Data scaling using RobustScaler:
![MON](https://user-images.githubusercontent.com/128135934/233820140-0e3f6bf8-025c-410c-be3f-13da10e2c9ab.png)

## RESULT:
Feature Generation process and Feature Scaling process is applied to the given data frames sucessfully.


