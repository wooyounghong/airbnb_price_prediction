# Predicting airbnb Price per Night: Linear Regression
## By: Alex Zieky and Wayne Wooyoung Hong

## Introduction
Alex and I created this project with dataset from New York City we found from insideairbnb.com to clean, to analyze airbnb statistics, and to be able to predict airbnb prices based on a dataset that was scraped around August of 2020. We will be using linear regression to come to conclusion. Our goal is to get users to be able to predict price of what their listing should be around. 

## Project
#### File Structure of the Repository
- Data_Cleaning.ipynb - This contains data cleaning of the dataset
- EDA_Analysis.ipynb - This contains visualizations and statistical test
- Modeling.ipynb - This contains our regression models
- graphs

#### Preprocessing
Our dataset consists of 46,527 rows and 74 columns. We have 1 target variable which is price. We created dummy variables using 'amentities', 'host_verification' and 'neighbourhood_group_cleansed' column. After looking at OLS summary of our columns, we dropped some columns due to multicollinearity and ended up with 104 columns.

#### Exploratory Data Analysis
##### Natural Log of Price Distribution


<img src="/graphs/log_price_dist.png" alt="Bedrooms vs price"/>
We ran a log transformation on price as it was initially skewed to the right. We have a bit closer to the normal distribution after log transformation but it is not fully normally distributed.



#### Bedrooms vs Price Distribution


<img src="/graphs/bedrooms_vs_price_after_outliers.png" alt="Bedrooms vs price"/>

Here we have a boxplot of our number of bedrooms and prices. When we first saw this chart, we saw that there were many outliers that did not make sense. We went through each observations to see if we can replace the values with correct data or replaced with 75% quartile.


#### Hypothesis Tests
For hypothesis tests, we set up our null and alternate hypothesis to see if we can reject or fail to reject the null hypothesis. We aimed to answer these following questions based on our target variable and features.
##### 1. Comparison of Prices in Manhattan, Queens, Staten Island, Brooklyn, and Bronx?
 
 
##### 2. Are prices of airbnb with air conditioning or no air conditioning same?


##### 3. Are the proportions of buroughs having kitchen equal or not equal?

#### Regression
###### 1. Normal Linear Regression
    - We found that the normal linear regression had RMSE of 25.305 for testing set and R SQUARED at 0.4818.
###### 2. Polynomial 
    - We found that the polynomial linear regression had training Root Mean Squared Error of 28.956103141815184 and R Squared at 0.3152. 
###### 3. Linear Regression using Feature Elimination Technique: SelectKBest()
    - We found that wiht feature elimination technique by using SelectKBest(), our RMSE for testing was 26.098703874094294 and Rsquared value at 26.098.

###### 4. Linear Regression using Recursive Feature Elimination
    - We found that by using Recursive Feature Elimination, we got a result of 25.307505621039958 for our RMSE. 
##### 5. Lasso    
    - We found that by using Lasso Regularization, we got a MRSE of 25.622307219892566.
##### 6. LassoCV
    - With LassoCV, we got a MRSE of 25.622307219892566 and Rsqaured value of 0.4924536892579856. Cross Validation goes through features and picks out the best features and runs the model based on that. 
    
    
    
    
### Conclusion

We feel that our model is not predictive we couldn't add all the values of our data in order to reduce the MRSE. As we ignored the outliers that had price higher than $256 since it will cause our MRSE to sky rocket to 100+. However, for lowered price dataset, we believe that linear regression with recursive feature elimination be our best fit as the MRSE was lowest out of all different models. 
