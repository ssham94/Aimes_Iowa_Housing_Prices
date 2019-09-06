# Project 2 - Ames Housing Data and Kaggle Challenge

## Problem Statement/Executive Summary

--------

In this project, we are trying to create a predictive model for housing prices in Ames, Iowa, using the dataset that was provided. The predictive model will generate pricing data for a testing set, and said data will be uploaded to Kaggle to check for accuracy of the model.

In this project, we will be exploring three different predictive models using Linear Regression, Ridge Regression, and Lasso Regression. After exploring all three, we will generate the RMSE (Root mean squared error) as well as R squared scores for each model, and compare the accuracy of the model. Using the R squared scores, we will be able to see if a model is over or underfit. We will also be comparing the the CV scores generated and compare them to the R squared scores. 

Aside from the competition aspect of Kaggle, and creating a predictive model, the primary goal for this project is to help those who are interested in investing or buying property in Ames, Iowa. By the end of this project, investors and homebuyers will be given the knowledge of what to look out for while buying a house in Ames Iowa.  

-------------

## Data Cleaning and EDA

Before diving into the data cleaning and EDA section of the project, a data dictionary can be found in the link below:

https://www.kaggle.com/c/dsi-us-7-project-2-regression-challenge/data

During initial exploration of data, a total of 81 columns of data, including sales price in the training data, could be found. Pool Quality, Misc Features, Alley, and Pool Area variables were dropped from the data due to having a large amount of null values found. All remaining null values were either turned to 0 or NA values depending on the variable. For the Lot Area variable, the average lot area was given to the missing null values, otherwise having a null value for lot area would indicate the lot didn't exist in the first place. In total, there were 19 nominal/categorical columns, 20 ordinal columns, and 38 numerical columns after dropping the columns mentioned before. The ordinal columns were then converted into a ranking system so that the ordinal columns could be used as variables. For the nominal and categorical columns, they were turned into dummy variables to be included in the models. 

Once the data was cleaned, a correlation between sales price and all the numerical/ordinal variables were created. Looking at the chart, only those with a correlation of 0.5 or higher were considered to be used as part of the model. While exploring the square footage variables, a feature of total square footage of the house was calculated by adding basement sqft, 1st floor sqft, 2nd floor sqft, and above grade livable area. Outlier data was found during the data cleaning process, specifically in total square footage, and lot area. All the outliers were removed from the dataset. 

-------------

## Preprocessing and Model

From the cleaned data, graphs for total square footage, year built, year remodeled, and overall quality vs sale price were created. From these graphs we could see that there was a generally good linear relationship for all four of these variables. Further exploration also shows that neighborhood data is also significant in the sense that each neighborhood can be ranked from least to most expensive. After further investigation, this can be due to numerous factors. However, from the data, it shows that basement quality is important due to the fact that iowa is known to have flooding problems due to tornadoes, therefore having a basement and a higher elevation to lower the chances of flooding is important while picking the neighborhood.

The following features were used for the model:
Total Square Footage
Overall Quality
Year Built
Year Remodeled
Ordinal Variables
Nominal/Categorical Variables

A baseline model was created for the features, and has a RMSE of 78317.520 for the training data and 78049.563 for the testing data. This baseline model was a simple model to test test the predictive sale price by only using only the total square footage as the only feature. A CV score was also created for the model, where there were 5 cross validations used. The average score was: 0.889212917984511

The following is a table of RMSE scores and R squared scores for linear, ridge, and lasso models:

Linear Regression:
Train RMSE score: 22912.307
Test RMSE score: 27021.363
Train R Squared Score: 0.9144106399614671
Test R Squared Score: 0.8798541417063039

Ridge Regression:
Train RMSE score: 23283.830
Test RMSE score: 27303.220
Train R Squared Score: 0.9116124725508927
Test R Squared Score: 0.8773346157419606

Lasso Regression:
Train RMSE score: 22913.924
Test RMSE score: 30014.040
Train R Squared Score: 0.914398560314544
Test R Squared Score: 0.8517675750099254

From these scores, we can see that they are generally well fit, where it utilizes about 90% of the data used for the model. Each regression also shows that they have an error of about 22 thousand to 30 thousand in worst case with the lasso regression. This means that they average price the model predicted is about 22 - 30 thousand dollars off the sale price. If we take the average sale price of the train set data which is about 180 thousand, than the errors is about a 12-17%. The RMSE scores have a significant improvement over the baseline model.

-------------

## Final Conclusions and Recommendations

From the different scores generated by the three models, the ridge regression model would be the best model to use. This is due to the fact that out of all the models, the ridge model has the smallest difference between the RMSE scores meaning that it was one of the more accurate models after using it on the test split data. The R squared scores were also closest to the average cross validation scores, indicating that the model wasn't suffering from high variance. 

The recommendation for home buyers in Ames Iowa would boil down to five main variables to look for while choosing a house:

Total Square Footage
Overall Quality
Year Built
Year Remodeled
Neighborhood

All supplementary data in the dataset would fall into one of these categories and only provide slight insights. For instance, basement quality would fall under overall quality, or number of bedrooms/bathrooms would fall under total square footage. Therefore, it is important to look at the overarching variables and consider the rest of the variables as supplementary. 

In future, hopefully neighborhood data can be provided ie. average neighborhood elevation, number of grocery stores/other amenities, etc. With neighborhood data, the sale price can be better inferred from data that has not been seen yet. If such data can be provided, the data will be checked and any insightful variables may be added to the predictive model. 

Final presentation link: 
https://docs.google.com/presentation/d/1tMiHUKCYPCSrUaUdyR7BxPEct_4hEn9-DV_vPKmZEJ4/edit?usp=sharing