# Factorization Machines<a name="fact-machines"></a>

A factorization machine is a general\-purpose supervised learning algorithm that you can use for both classification and regression tasks\. It is an extension of a linear model that is designed to capture interactions between features within high dimensional sparse datasets economically\. For example, in a click prediction system, the factorization machine model can capture click rate patterns observed when ads from a certain ad\-category are placed on pages from a certain page\-category\. Factorization machines are a good choice for tasks dealing with high dimensional sparse datasets, such as click prediction and item recommendation\.

**Note**  
The Amazon SageMaker implementation of factorization machines considers only pair\-wise \(2nd order\) interactions between features\.

**Topics**
+ [Input/Output Interface](#fm-inputoutput)
+ [EC2 Instance Recommendation](#fm-instances)
+ [Factorization Machines Sample Notebooks](#fm-sample-notebooks)
+ [How Factorization Machines Work](fact-machines-howitworks.md)
+ [Factorization Machines Hyperparameters](fact-machines-hyperparameters.md)
+ [Tuning a Factorization Machines Model](fm-tuning.md)
+ [Factorization Machine Response Formats](fm-in-formats.md)

## Input/Output Interface<a name="fm-inputoutput"></a>

The factorization machine algorithm can be run in either in binary classification mode or regression mode\. In each mode, a dataset can be provided to the test channel along with the train channel dataset\. In regression mode, the testing dataset is scored using Root Mean Square Error \(RMSE\)\. In binary classification mode, the test dataset is scored using Binary Cross Entropy \(Log Loss\), Accuracy \(at threshold=0\.5\) and F1 Score \(at threshold =0\.5\)\.

The factorization machines algorithm currently supports training only on the `recordIO-protobuf` format with `Float32` tensors\. Because their use case is predominantly on sparse data, `CSV` is not a good candidate\. Both File and Pipe mode training are supported for recordIO\-wrapped protobuf\.

For inference, factorization machines support the `application/json` and `x-recordio-protobuf` formats\. For binary classification models, both the score and the predicted label are returned\. For regression, just the score is returned\.

Please see example notebooks for more details on training and inference file formats\.

## EC2 Instance Recommendation<a name="fm-instances"></a>

The Amazon SageMaker Factorization Machines algorithm is highly scalable and can train across distributed instances\. We recommend training and inference with CPU instances for both sparse and dense datasets\. In some circumstances, training with one or more GPUs on dense data might provide some benefit\. Training with GPUs is available only on dense data\. Use CPU instances for sparse data\.

## Factorization Machines Sample Notebooks<a name="fm-sample-notebooks"></a>

For a sample notebook that uses the Amazon SageMaker factorization machine learning algorithm to analyze the images of handwritten digits from zero to nine in the MNIST dataset, see [An Introduction to Factorization Machines with MNIST](https://github.com/awslabs/amazon-sagemaker-examples/blob/master/introduction_to_amazon_algorithms/factorization_machines_mnist/factorization_machines_mnist.ipynb)\. For instructions how to create and access Jupyter notebook instances that you can use to run the example in Amazon SageMaker, see [Using Notebook Instances](nbi.md)\. Once you have created a notebook instance and opened it, select the **SageMaker Examples** tab to see a list of all the Amazon SageMaker samples\. The topic modeling example notebooks using the NTM algorithms are located in the **Introduction to Amazon algorithms** section\. To open a notebook, click on its **Use** tab and select **Create copy**\.