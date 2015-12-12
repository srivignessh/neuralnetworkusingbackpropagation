Recognizing Faces using a Two-layer
Perceptron


The main method to train the two-layer perceptron is trainStochasticSquaredErrorTwoLayerPerceptron. The method applies stochastic training (or to be precise a stochastic variant of mini-batch training) using the sum-of-squared error function and the error backpropagation algorithm.

function [hiddenWeights, outputWeights, error] = trainStochasticSquaredErrorTwoLayerPerceptron(activationFunction, dActivationFunction, numberOfHiddenUnits, inputValues, targetValues, epochs, batchSize, learningRate)
% trainStochasticSquaredErrorTwoLayerPerceptron Creates a two-layer perceptron
% and trains it on the MNIST dataset.
%
% INPUT:
% activationFunction             : Activation function used in both layers.
% dActivationFunction            : Derivative of the activation
% function used in both layers.
% numberOfHiddenUnits            : Number of hidden units.
% inputValues                    : Input values for training (784 x 60000)
% targetValues                   : Target values for training (1 x 60000)
% epochs                         : Number of epochs to train.
% batchSize                      : Plot error after batchSize images.
% learningRate                   : Learning rate to apply.
%
% OUTPUT:
% hiddenWeights                  : Weights of the hidden layer.
% outputWeights                  : Weights of the output layer.
% 

The above method requires the activation function used for both the hidden and the output layer to be given as parameter. I used the logistic sigmoid activation function:

function y = logisticSigmoid(x)
% simpleLogisticSigmoid Logistic sigmoid activation function
% 
% INPUT:
% x     : Input vector.
%
% OUTPUT:
% y     : Output vector where the logistic sigmoid was applied element by
% element.
%

In addition, the error backpropagation algorithm needs the derivative of the used activation function:

function y = dLogisticSigmoid(x)
% dLogisticSigmoid Derivative of the logistic sigmoid.
% 
% INPUT:
% x     : Input vector.
%
% OUTPUT:
% y     : Output vector where the derivative of the logistic sigmoid was
% applied element by element.
%

The method applyStochasticSquaredErrorTwoLayerPerceptronMNIST uses both the training method seen above and the method validateTwoLayerPerceptron to evaluate the performance of the two-layer perceptron:

function [correctlyClassified, classificationErrors] = validateTwoLayerPerceptron(activationFunction, hiddenWeights, outputWeights, inputValues, labels)
% validateTwoLayerPerceptron Validate the twolayer perceptron using the
% validation set.
%
% INPUT:
% activationFunction             : Activation function used in both layers.
% hiddenWeights                  : Weights of the hidden layer.
% outputWeights                  : Weights of the output layer.
% inputValues                    : Input values for training (784 x 10000).
% labels                         : Labels for validation (1 x 10000).
%
% OUTPUT:
% correctlyClassified            : Number of correctly classified values.
% classificationErrors           : Number of classification errors.
% 

License

Copyright 2013 - 2014 David Stutz

The application is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

The application is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

See http://www.gnu.org/licenses/.
