# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Import the necessary packages using import statement.

2. Read the given csv file using read_csv() method and print the number of contents to be displayed using df.head().

3. Import KMeans and use for loop to cluster the data.

4. Predict the cluster and plot data graphs.

5. Print the outputs and end the program 
## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: THEJASWINI D
RegisterNumber: 212223110059
*/
```

```
import pandas as pd
import matplotlib.pyplot as plt
data=pd.read_csv("/content/Mall_Customers.csv")
data
```
![Screenshot 2024-10-30 102624](https://github.com/user-attachments/assets/1aaea802-4893-4cf1-8e84-35bea00b82fe)


```
data.head(7)
```
![Screenshot 2024-10-30 102636](https://github.com/user-attachments/assets/fdea8080-4256-4c01-b825-1f396d5ea26c)

```
data.info()
```
![Screenshot 2024-10-30 102645](https://github.com/user-attachments/assets/9f6c02c8-2093-43c4-b13d-348e9ebdb589)

```
data.isnull().sum()
```
![Screenshot 2024-10-30 102653](https://github.com/user-attachments/assets/10aaa727-d935-48a4-99f7-877db99946ee)

```
from sklearn.cluster import KMeans
wcss=[]
for i in range(1,11):
  kmeans=KMeans(n_clusters=i,init="k-means++")
  kmeans.fit(data.iloc[:,3:])
  wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("Number of clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
```
![Screenshot 2024-10-30 102703](https://github.com/user-attachments/assets/862cece2-d6c1-4808-9995-a10197c0d4df)

```
km=KMeans(n_clusters=5)
km.fit(data.iloc[:,3:])
```
![Screenshot 2024-10-30 104000](https://github.com/user-attachments/assets/4c9fdbf2-04fe-44c9-820c-50f1beb7ae2f)

```
y_pred=km.predict(data.iloc[:,3:])
y_pred
```
![Screenshot 2024-10-30 104006](https://github.com/user-attachments/assets/9b6ae820-8d23-4a99-ab6f-1522dd522245)

```
data["cluster"]=y_pred
data
```
![Screenshot 2024-10-30 104015](https://github.com/user-attachments/assets/4ff4b4ce-b36e-466b-b7ea-059c4b74ca2e)

```
df0=data[data["cluster"]==0]
df1=data[data["cluster"]==1]
df2=data[data["cluster"]==2]
df3=data[data["cluster"]==3]
df4=data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="blue",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="green",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="orange",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="purple",label="cluster4")
plt.legend()
plt.title("Customer Segments")
```
## Output:
![Screenshot 2024-10-30 105150](https://github.com/user-attachments/assets/ddac9111-b3c9-4c67-a619-1350dc5982e4)


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
