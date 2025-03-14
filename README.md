# E-commerce Customer Spending Prediction

## Overview
This project involves analyzing an e-commerce dataset and building a predictive model to estimate a customer's yearly spending based on their session behavior. The dataset includes various customer attributes such as session length, time spent on an app, and membership duration.

## Dataset Details
**File Name:** `ecommerce-customers_1740850429129.csv`

### Columns:
- **Email**: Unique customer identifier
- **Address**: Customer's location
- **Avatar**: Customer's profile image color
- **Avg. Session Length**: Average time a user spends on the e-commerce platform
- **Time on App**: Time spent using the mobile app
- **Time on Website**: Time spent on the website
- **Length of Membership**: Number of years the customer has been a member
- **Yearly Amount Spent**: Total spending by the customer in a year (Target variable)

## Objective
To develop a regression model that predicts the yearly amount spent by a customer based on their interaction with the e-commerce platform.

## Implementation Steps

### 1. Data Preprocessing
- Load the dataset using pandas
- Check for missing values
- Perform descriptive statistics

### 2. Exploratory Data Analysis (EDA)
- Univariate analysis (boxplots for session time, app time, website time, etc.)
- Bivariate analysis (correlation and scatter plots)
- Visualizations using matplotlib and seaborn

### 3. Feature Engineering
- Selecting relevant features: `Avg. Session Length`, `Time on App`, `Time on Website`, `Length of Membership`
- Splitting dataset into training and test sets (70% training, 30% testing)

### 4. Model Training
- Train a **Linear Regression Model** using scikit-learn
- Fit the model to the training data
- Predict yearly spending on the test dataset

### 5. Model Evaluation
- Compute **R² score** to measure model accuracy
- Scatter plot for actual vs. predicted values

### 6. Prediction on New Data
- Provide a sample input for a new customer
- Predict their estimated yearly spending

## Technologies Used
- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn

## Results
- The model achieved an **R² score of 0.98**, indicating strong predictive performance.
- The most influential factor affecting yearly spending was **Length of Membership**.

## Usage
To run the project, follow these steps:

```python
# Import necessary libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import r2_score

# Load dataset
dataset = pd.read_csv('ecommerce-customers_1740850429129.csv')

# Define features and target variable
X = dataset[['Avg. Session Length', 'Time on App', 'Time on Website', 'Length of Membership']]
Y = dataset['Yearly Amount Spent']

# Split into training and testing
X_train, X_test, y_train, y_test = train_test_split(X, Y, test_size=0.3, random_state=50)

# Train model
lm = LinearRegression()
lm.fit(X_train, y_train)

# Predictions
pred = lm.predict(X_test)

# Model performance
print("R² Score:", r2_score(y_test, pred))

# Scatter plot for predictions vs actual
plt.scatter(y_test, pred, color='g')
plt.xlabel('Actuals')
plt.ylabel('Predictions')
plt.show()
```

## Future Enhancements
- Explore more complex models such as **Decision Trees** or **Random Forests**
- Implement **feature engineering** to enhance predictions
- Deploy the model as an **API** for real-time predictions
