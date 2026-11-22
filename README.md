# EXPERIMENT NO.2: EXPLORATORY DATA ANALYSIS (EDA)


## AIM

To perform Exploratory Data Analysis (EDA) on the heart disease dataset to understand the data distribution, relationships, and key patterns useful for business insights and model building.



## DATASET

The dataset used for this experiment is `heartdisease.csv`. It contains medical and demographic information such as age, sex, cholesterol levels (`totChol`), `BMI`, blood pressure, and target values (`TenYearCHD`) indicating heart disease presence.


## ALGORITHM

1. Import required Python libraries (`numpy`, `pandas`, `seaborn`, `matplotlib`).
2. Load the dataset into a Pandas DataFrame.
3. Display the dataset structure, shape, and descriptive statistics.
4. Check for missing values and duplicate rows.
5. Examine correlations among numeric features using a correlation matrix and heatmap.
6. Visualize univariate distributions using histograms, boxplots, and countplots.
7. Analyze bivariate and multivariate relationships using scatter plots and pairplots.



## FUNCTIONS AND METHODS USED

| Category | Function / Method | Purpose / Description |
| :--- | :--- | :--- |
| **Basic Exploration** | `df.info()` | Inspect dataset structure and data types |
| | `df.describe()` | Generate descriptive statistics |
| | `df.isnull().sum()` | Detect missing values in each column |
| | `df.duplicated().sum()` | Identify duplicate rows |
| | `df.corr()` | Find correlations between numeric variables |
| **Univariate Analysis** | `sns.histplot()` | Plot histogram (distribution of single variable) |
| | `sns.boxplot()` | Identify outliers using boxplot |
| | `sns.countplot()` | Count occurrences of categorical variables |
| **Bivariate Analysis** | `sns.scatterplot()` | Display relationship between two variables |
| | `sns.heatmap()` | Show correlation matrix visually |
| **Multivariate Analysis** | `sns.pairplot()` | Show pairwise relationships across variables |
| **Visualization Controls** | `plt.figure()`, `plt.title()`, `plt.xlabel()`, `plt.ylabel()`, `plt.show()` | Configure and display plotted charts |


## PROGRAM AND OUTPUT

import numpy as np  
import pandas as pd  
import seaborn as sns  
import matplotlib.pyplot as plt  
df = pd.read_csv('/content/drive/MyDrive/heartdisease.csv')  
print("Dataset Shape:", df.shape)  
print("\n--- Dataset Info ---")  
df.info()  
print("\n--- Descriptive Statistics ---")  
print(df.describe())  
print("\n--- Missing Values per Column ---")  
print(df.isnull().sum())  
print("\nTotal Duplicate Rows:", df.duplicated().sum())  
numeric_df = df.drop(columns=['S. No']).select_dtypes(include=[np.number])  
corr_matrix = numeric_df.corr()  
print("\n--- Correlation Matrix ---")  
print(corr_matrix)  
plt.figure(figsize=(12, 9))  
sns.heatmap(corr_matrix, annot=True, fmt=".2f", cmap="coolwarm", linewidths=0.5)  
plt.title("Correlation Heatmap of Numeric Features")  
plt.xlabel("Features")  
plt.ylabel("Features")  
plt.show()  
plt.figure(figsize=(8, 4))  
sns.histplot(df['Age'], kde=True, bins=15, color='steelblue')  
plt.title("Age Distribution")  
plt.xlabel("Age (Years)")  
plt.ylabel("Frequency")  
plt.show()  
plt.figure(figsize=(8, 4))  
sns.boxplot(x=df['Totalcholestrol'], color='coral')  
plt.title("Total Cholesterol Boxplot (Outlier Detection)")  
plt.xlabel("Total Cholesterol (mg/dL)")  
plt.show()  
plt.figure(figsize=(6, 4))  
sns.countplot(x='TenYearCHD', data=df, hue='TenYearCHD', palette='viridis', legend=False)  
plt.title("10-Year CHD Target Count")  
plt.xlabel("TenYearCHD (0 = No, 1 = Yes)")  
plt.ylabel("Patient Count")  
plt.show()  
plt.figure(figsize=(8, 5))  
sns.scatterplot(x='Age', y='SysBP', hue='TenYearCHD', data=df, palette='Set1')  
plt.title("Bivariate Analysis: Age vs. Systolic Blood Pressure")  
plt.xlabel("Age (Years)")  
plt.ylabel("Systolic Blood Pressure (SysBP)")  
plt.show()  
selected_features = ['Age', 'Totalcholestrol', 'SysBP', 'BMI', 'Glucose', 'TenYearCHD']  
sns.pairplot(df[selected_features], hue='TenYearCHD', palette='husl', diag_kind='kde')  
plt.suptitle("Multivariate Pairplot of Key Health Metrics", y=1.02)  
plt.show()  

<img width="445" height="617" alt="image" src="https://github.com/user-attachments/assets/298b986e-cbb7-4073-8c2d-8c945ce8bf4f" />
<img width="417" height="608" alt="image" src="https://github.com/user-attachments/assets/25593e1c-0b21-4ae7-85bb-db9a40f3d910" />
<img width="412" height="170" alt="image" src="https://github.com/user-attachments/assets/865c63d3-5cdb-4e7d-8588-ecac6190bd62" />
<img width="646" height="545" alt="image" src="https://github.com/user-attachments/assets/630b7c99-dc30-4885-b939-d2942452027f" />
<img width="431" height="497" alt="image" src="https://github.com/user-attachments/assets/cb89cbb1-ccf6-41af-af98-1ee624844510" />
<img width="440" height="557" alt="image" src="https://github.com/user-attachments/assets/cd631537-9867-4cd6-bc28-619202b261b9" />
<img width="665" height="626" alt="image" src="https://github.com/user-attachments/assets/0d653ae6-72db-4394-bb10-3dd10c87620e" />







## RESULT 

Exploratory Data Analysis (EDA) on the heartdisease.csv dataset (250 records, 17 features) confirmed clean data with no missing values or duplicates, and an 18.4% prevalence of 10-year CHD risk.


