# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```
import pandas as pd
df= pd.read_csv("/content/SAMPLEIDS (2).csv")
df
```
 <img width="1079" height="859" alt="image" src="https://github.com/user-attachments/assets/e7737cd3-dd5d-4b5d-889d-cbde9a2c6927" />

```
df.head()
```

<img width="1042" height="247" alt="image" src="https://github.com/user-attachments/assets/6cccee6d-20e9-41e3-b324-b5e5a25aaae0" />

```
df.tail()
```
<img width="1069" height="258" alt="image" src="https://github.com/user-attachments/assets/0c206b3f-7007-443f-b807-3537501bc4a9" />

```
df.head(3)
```
<img width="1032" height="177" alt="image" src="https://github.com/user-attachments/assets/9d09fc03-eede-4f73-ba8d-51fb379119b9" />

```
df.tail(3)
```
<img width="1079" height="190" alt="image" src="https://github.com/user-attachments/assets/5afea8ee-fb59-4580-92f9-6ca39cfcc01f" />

```
df.isnull()
```
<img width="870" height="857" alt="image" src="https://github.com/user-attachments/assets/1de69b83-4966-46f0-abe9-1aa9142f92bd" />

```
df.isnull().sum()
```
<img width="715" height="576" alt="image" src="https://github.com/user-attachments/assets/52adfc40-5269-41e3-b6b5-75bee5721dd1" />

```
df.isnull().any()
```
<img width="545" height="574" alt="image" src="https://github.com/user-attachments/assets/c308edd2-0525-4f16-a67e-3fcfe53a56eb" />

```
df.dropna()
```
<img width="1080" height="585" alt="image" src="https://github.com/user-attachments/assets/91c06570-6d74-4b7a-b426-58e4a577bc65" />

```
df.fillna(5)
```
<img width="1071" height="838" alt="image" src="https://github.com/user-attachments/assets/2328f3b3-51e9-477f-af5f-c146f15824f2" />

```
df.fillna(method = 'ffill')
```
<img width="1095" height="857" alt="image" src="https://github.com/user-attachments/assets/c97281e4-47c7-45f1-b8de-9d2702d66228" />

```
df.fillna(method = 'bfill')
```
<img width="1077" height="863" alt="image" src="https://github.com/user-attachments/assets/3087f41b-cdf9-485f-8768-962147b719e5" />

```
df.fillna({'GENDER': 'MALE','NAME':'RAM','TOTAL':602.5,'AVG':108.057777})
```
<img width="1076" height="859" alt="image" src="https://github.com/user-attachments/assets/152798ed-d084-4e05-aae2-83d137614fdf" />

```
ir = pd.read_csv('iris.csv')
ir
```
<img width="723" height="512" alt="image" src="https://github.com/user-attachments/assets/f631e6fc-4952-4a2f-b5d3-18695e165223" />

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
<img width="790" height="604" alt="image" src="https://github.com/user-attachments/assets/e2519aa2-0dbe-45e8-be06-98f2fe697a11" />

```
Q1= ir.sepal_width.quantile(0.25)
Q3= ir.sepal_width.quantile(0.75)
IQR= Q3-Q1
print(IQR )
```
<img width="429" height="43" alt="image" src="https://github.com/user-attachments/assets/d0911872-9abf-4566-a3de-69e3abd6be1d" />

```
rid=ir[((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
rid['sepal_width']
```
<img width="530" height="272" alt="image" src="https://github.com/user-attachments/assets/9f091002-6da6-4f9c-ac0b-7d1cb4395b3b" />

```
rid=ir[~((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
rid['sepal_width']
```
<img width="573" height="588" alt="image" src="https://github.com/user-attachments/assets/ce56985b-31a1-4024-ae50-7e29b9fd9df8" />

```
sns.boxplot(x='sepal_width',data= rid)
```
<img width="826" height="595" alt="image" src="https://github.com/user-attachments/assets/81e20792-8fda-478b-b203-80a7d5f94cdd" />

```
import numpy as np
import scipy.stats as stats
Z= np.abs(stats.zscore(ir['sepal_width']))
Z
```
<img width="840" height="680" alt="image" src="https://github.com/user-attachments/assets/4b25b8ee-0f7c-4f5e-be4d-1212d6412a4a" />

```
df1 = ir[Z<3]
df1
```
<img width="729" height="512" alt="image" src="https://github.com/user-attachments/assets/b19f3b99-7ce7-4c81-a7d4-7135b0c2657c" />

# Result

The given data has been successfully read, cleaned by handling duplicates and missing values, and saved to a new file named cleaned_data.csv.         
