# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 2: Regression model for Ames Iowa Housing Dataset

# Overview
Ames is a town in Iowa with a population of 66,023. Ames is in Story County and is one of the best places to live in Iowa. Living in Ames offers residents an urban suburban mix feel and most residents rent their homes. In Ames there are a lot of bars, coffee shops, and parks. Many young professionals live in Ames and residents tend to lean conservative. The public schools in Ames are highly rated.

# Problem Statement
As part of real estate investor - analytics team, I will be analysing the Aimes Iowa Housing Data set to give a suggestion on top 10 features that can give a good housing sales price.

As a real estate investor, it is necessary to see trends when purchasing a house in hopes that we can make profit from selling or renting a house. One of the ways is to just see what are the top 10 features that buyers look out for and are willing to pay high price for the house that they are interested in.

In the later part of this notebook, I have attempted to predict the saleprice of the houses with features that are already tabulated in, called Test.CSV

# Contents:

- [Overview](#Overview)
- [Poblem Statement](#Problem-Statement)
- [Data fields](#Data-fields)
- [Data Clean Up](#Data-Clean-Up)
- [Exploratory Analysis](#Exploratory-Analysis)
- [Conclusions and Recommendations](#Conclusions-and-Recommendations)

# Data fields

SalePrice - the property's sale price in dollars. This is the target variable that you're trying to predict.  
MSSubClass: The building class  
MSZoning: The general zoning classification  
LotFrontage: Linear feet of street connected to property  
LotArea: Lot size in square feet  
Street: Type of road access  
Alley: Type of alley access  
LotShape: General shape of property  
LandContour: Flatness of the property  
Utilities: Type of utilities available  
LotConfig: Lot configuration  
LandSlope: Slope of property  
Neighborhood: Physical locations within Ames city limits  
Condition1: Proximity to main road or railroad  
Condition2: Proximity to main road or railroad (if a second is present)  
BldgType: Type of dwelling  
HouseStyle: Style of dwelling  
OverallQual: Overall material and finish quality    
OverallCond: Overall condition rating  
YearBuilt: Original construction date  
YearRemodAdd: Remodel date  
RoofStyle: Type of roof  
RoofMatl: Roof material  
Exterior1st: Exterior covering on house  
Exterior2nd: Exterior covering on house (if more than one material)  
MasVnrType: Masonry veneer type  
MasVnrArea: Masonry veneer area in square feet  
ExterQual: Exterior material quality  
ExterCond: Present condition of the material on the exterior  
Foundation: Type of foundation  
BsmtQual: Height of the basement  
BsmtCond: General condition of the basement  
BsmtExposure: Walkout or garden level basement walls  
BsmtFinType1: Quality of basement finished area  
BsmtFinSF1: Type 1 finished square feet  
BsmtFinType2: Quality of second finished area (if present)  
BsmtFinSF2: Type 2 finished square feet  
BsmtUnfSF: Unfinished square feet of basement area  
TotalBsmtSF: Total square feet of basement area  
Heating: Type of heating  
HeatingQC: Heating quality and condition  
CentralAir: Central air conditioning  
Electrical: Electrical system  
1stFlrSF: First Floor square feet  
2ndFlrSF: Second floor square feet  
LowQualFinSF: Low quality finished square feet (all floors)  
GrLivArea: Above grade (ground) living area square feet  
BsmtFullBath: Basement full bathrooms  
BsmtHalfBath: Basement half bathrooms  
FullBath: Full bathrooms above grade  
HalfBath: Half baths above grade  
Bedroom: Number of bedrooms above basement level  
Kitchen: Number of kitchens  
KitchenQual: Kitchen quality  
TotRmsAbvGrd: Total rooms above grade (does not include bathrooms)  
Functional: Home functionality rating  
Fireplaces: Number of fireplaces  
FireplaceQu: Fireplace quality  
GarageType: Garage location  
GarageYrBlt: Year garage was built  
GarageFinish: Interior finish of the garage  
GarageCars: Size of garage in car capacity  
GarageArea: Size of garage in square feet  
GarageQual: Garage quality  
GarageCond: Garage condition  
PavedDrive: Paved driveway  
WoodDeckSF: Wood deck area in square feet  
OpenPorchSF: Open porch area in square feet  
EnclosedPorch: Enclosed porch area in square feet  
3SsnPorch: Three season porch area in square feet  
ScreenPorch: Screen porch area in square feet  
PoolArea: Pool area in square feet  
PoolQC: Pool quality  
Fence: Fence quality  
MiscFeature: Miscellaneous feature not covered in other categories  
MiscVal: Value of miscellaneous feature  
MoSold: Month Sold  
YrSold: Year Sold  
SaleType: Type of sale  
SaleCondition: Condition of sale  

# Data Clean Up
There are quite a number of rows with null values. 
Lot Frontage values were filled with the median value.
Ordinal features are mapped with their ordinal values.
Features that are nominal are mapped with 0 after looking through it.
One hot encoding was done: dummify features that are nominal values.

# Exploratory Analysis
Correlation plot was plotted. Top 10 features that have highest correlation with saleprice are:overallqual,exterqual,grlivarea,kitchenqual,garagearea,garagecars,totalbsmtsf,1stflrsf,bsmtqual,yearbuilt

Boxplots was plotted to seek outliers in features. 

# Conclusions and Recommendations

Linear regression with Lasso Regularization is selected as best model. 
Best alpha: alpha=129.765
Difference in MSE Scores: 0.29923395858967305 %

the top 10 features that the model predict are:  

1) Stone Brook neighbourhood   
2) Northridge Heights neighbourhood  
3) Misc Features: 2nd Garage  
4) Northridge Neighbourhood  
5) Green Hills Neighbourhood  
6) Proximity to various conditions: Near positive off-site feature--park, greenbelt, etc.  
7) Sale Type: Home just constructed and sold  
8) Landcontour: flatness of property: Hillside - Significant slope from side to side  
9) Evaluates the quality of the material on the exterior  
10) Crawford Neighbourhood  

From this results, what I can infer is that neighbourhood is important at fetching higher saleprice. My company could look into houses that are located in these neighbourhoods, do a small scale renovations and sell them at a much higher price after as a business as well. 
Things that can be improved on in the future:

1) removal of outliers in the features and  re-run the model to see if this affects our model and in return, gives different top features compared to my results

2) diagnosing on multicollinearity using : The variance inflation factor (VIF) quantifies the extent of correlation between one predictor and the other predictors in a model.Higher values signify that it is difficult to impossible to assess accurately the contribution of predictors to a model.

This can be done by doing further feature engineering and run a model to compare the results, such as:

- removal of features that are pretty similar( example:landslope as there is landcontour already)   
- creating new features (such as age of the house etc)
- try different model: ridge, kbest to compare the results #AmesIowaHousingPrediction
