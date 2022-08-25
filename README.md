# Charity Funding Predictor
Nonprofit foundation Alphabet Soup is looking for a tool to predict whether applicants they fund will be successful. 

The neural network model being built is based on a [CSV](Resources/charity_data.csv) containing data on organizations that have received funding. Included columns:

* `EIN` and `NAME` - Identification columns
* `APPLICATION_TYPE` - Alphabet Soup application type
* `AFFILIATION` - Affiliated sector of industry
* `CLASSIFICATION` - Government organization classification
* `USE_CASE` - Use case for funding
* `ORGANIZATION` - Organization type
* `STATUS` - Active status
* `INCOME_AMT` - Income classification
* `SPECIAL_CONSIDERATIONS` - Special considerations for application
* `ASK_AMT` - Funding amount requested
* `IS_SUCCESSFUL` - Was the money used effectively

## Step 1: Data Preprocessing
Steps 1 and 2 take place in the [fund_predictor](fund_predictor.ipynb) notebook. The specified steps were followed:

1. Read in the CSV and remove `EIN` and `NAME` columns
2. Determine number of unique values in each column
3. Using cutoff values, bin "rare" categorical values into category "Other" for columns `APPLICATION_TYPE` and `CLASSIFICATION`
4. Encode categorical variables with `Pandas.get_dummies()`

## Step 2: Compile, Train, and Evaluate the Model
The stated steps were followed:

1. Create a neural network using `tensorflow.keras`
2. Add two hidden layers with the "ReLU" activation function
3. Add an output layer with the "sigmoid" activation function
4. Compile and train the model, saving the model's weights every 5 epochs
5. Evaluate the model's loss and accuracy with test data
6. Save the [model](Model/AlphabetSoupCharity.h5) to an HDF5 file

## Step 3: Optimization
Optimization takes place in a separate notebook called [AlphabetSoupCharity_Optimization](AlphabetSoupCharity_Optimization.ipynb).

The goal of optimization was to reach a target predictive accuracy higher than 75%. This goal was achieved by reintroducing the `NAME` column and reducing the number of nodes active in each hidden layer. 

## Step 4: Analysis 
Through the optimization process, the accuracy of the model increased from around 72% to just under 79%.

The full [analysis report](AlphabetSoup_Analysis.md) is available to read at the link. 