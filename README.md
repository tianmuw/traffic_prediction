# traffic_prediction
## Introduction
This project aims to develop a Gradient Boosting Decision Tree (GBDT) algorithm that can predict short-term traffic
flow values based on previous traffic flow data. The training, validation, and testing data used in this project 
are obtained from PeMS and are for the Freeway SR52-E in District 11 (San Diego). The features of the data include 
previous VMT, VHT, Month, Day, Hour, number of lane points, and the percentage of observed cars.

GBDT is a well-developed machine learning algorithm in classification and regression fields that requires scanning 
all the data instances to estimate the information gain of all possible split points. In this case, the prediction 
of VMT could be used to estimate the rough lane occupancy, which might provide information to help schedule the maintenance plan.

## Testing example
To test the model, run the GBDT_reg_test.py file. If you want to test the existing model, you can comment out the following 
lines in the GBDT_reg_test.py file:
```
model = GBDTRegressor()
model.fit(X_train, y_train, X_valid, y_valid)
pickle.dump(model, open("pima.pickle_test_Last3.dat", "wb"))
```

## Data
The Train and Test files contain examples of training and testing data. If you want to test/train more data, 
please download the original data from PeMS and process the data in a similar format.

## Data split
The training and validation data are from 2021, and they are randomly scrambled. 70% of the data is assigned 
as training data, and the remaining 30% is validation data.

## Tunable parameter
The accuracy of the GBDT can be changed by tuning the number of CART estimators, the learning rate, and some 
stopping criteria in the GBDT.py file. The loss function and corresponding gradient can also be changed in the GBDT.py file.

## Results
The resulting error is the mean absolute percentage error, and the accuracy is the prediction that with error less than 20%
