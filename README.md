# Implementation-of-Linear-Regression-Using-Gradient-Descent

## AIM:
To write a program to predict the profit of a city using the linear regression model with gradient descent.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Load the dataset from a CSV file and separate the features and target variable, encoding any categorical variables as needed.
2. Scale the features using a standard scaler to normalize the data.
3. Initialize model parameters (theta) and add an intercept term to the feature set.
4. Train the linear regression model using gradient descent by iterating through a specified number of iterations to minimize the cost function.
5. Make predictions on new data by transforming it using the same scaling and encoding applied to the training data. 

## Program:
```
/*
Program to implement the linear regression using gradient descent.
Developed by: Pradeep E
RegisterNumber:  212223230149
*/
import numpy as np 
import pandas as pd
from sklearn.preprocessing import StandardScaler
def linear_regression(X1,y,learning_rate=0.01,num_iters=1000):
    X=np.c_[np.ones(len(X1)),X1]
    theta=np.zeros(X.shape[1]).reshape(-1,1)
    for _ in range(num_iters):
        predictions = (X).dot(theta).reshape(-1,1)
        errors=(predictions -y).reshape(-1,1)
        theta -= learning_rate * (1/len(X1)) * X.T.dot(errors)
    return theta
data=pd.read_csv('startup.csv')
print(data.head())
X=(data.iloc[1:, :-2].values)
print(X)
X1=X.astype(float)
scaler=StandardScaler()
y=(data.iloc[1:,-1].values).reshape(-1,1)
print(y)
X1_Scaled=scaler.fit_transform(X1)
Y1_Scaled=scaler.fit_transform(y)
print(X1_Scaled)
print(Y1_Scaled)

theta=linear_regression(X1_Scaled,Y1_Scaled)
new_data=np.array([165349.2,136897.8,471784.1]).reshape(-1,1)
new_Scaled=scaler.fit_transform(new_data)
prediction=np.dot(np.append(1, new_Scaled), theta)
prediction=prediction.reshape(-1,1)
pre=scaler.inverse_transform(prediction)
print(f"prediction value: {pre}")
```

## Output:

![Screenshot 2024-09-01 171506](https://github.com/user-attachments/assets/ec75ae71-7cb9-4450-bb95-f44201f9e8e8)
![Screenshot 2024-09-01 171535](https://github.com/user-attachments/assets/2610cdb8-766c-4557-acc4-6cb9863ad771)

## Result:
Thus the program to implement the linear regression using gradient descent is written and verified using python programming.
