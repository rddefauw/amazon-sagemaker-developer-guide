# CatBoost hyperparameters<a name="catboost-hyperparameters"></a>

The following table contains the subset of hyperparameters that are required or most commonly used for the Amazon SageMaker CatBoost algorithm\. Users set these parameters to facilitate the estimation of model parameters from data\. The SageMaker CatBoost algorithm is an implementation of the open\-source [CatBoost](https://github.com/catboost/catboost) package\.

**Note**  
The default hyperparameters are based on example datasets in the [CatBoost sample notebooks](catboost.md#catboost-sample-notebooks)\.

By default, the SageMaker CatBoost algorithm automatically chooses an evaluation metric and loss function based on the type of classification problem\. The CatBoost algorithm detects the type of classification problem based on the number of labels in your data\. For regression problems, the evaluation metric and loss functions are both root mean squared error\. For binary classification problems, the evaluation metric is Area Under the Curve \(AUC\) and the loss function is log loss\. For multiclass classification problems, the evaluation metric and loss functions are multiclass cross entropy\. You can use the `eval_metric` hyperparameter to change the default evaluation metric\. Refer to the following table for more information on LightGBM hyperparameters, including descriptions, valid values, and default values\.


| Parameter Name | Description | 
| --- | --- | 
| iterations |  The maximum number of trees that can be built\. Valid values: integer, range: Positive integer\. Default value: `500`\.  | 
| early\_stopping\_rounds |  The training will stop if one metric of one validation data point does not improve in the last `early_stopping_rounds` round\. If `early_stopping_rounds` is less than or equal to zero, this hyperparameter is ignored\. Valid values: integer\. Default value: `5`\.  | 
| eval\_metric |  The evaluation metric for validation data\. If `eval_metric` is set to the default `"auto"` value, then the algorithm automatically chooses an evaluation metric based on the type of classification problem: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/sagemaker/latest/dg/catboost-hyperparameters.html) Valid values: string, refer to the [CatBoost documentation](https://catboost.ai/en/docs/references/eval-metric__supported-metrics) for valid values\. Default value: `"auto"`\.  | 
| learning\_rate |  The rate at which the model weights are updated after working through each batch of training examples\. Valid values: float, range: \(`0.0`, `1.0`\)\. Default value: `0.009`\.  | 
| depth |  Depth of the tree\. Valid values: integer, range: \(`1`, `16`\)\. Default value: `6`\.  | 
| l2\_leaf\_reg |  Coefficient for the L2 regularization term of the cost function\. Valid values: integer, range: Positive integer\. Default value: `3`\.  | 
| random\_strength |  The amount of randomness to use for scoring splits when the tree structure is selected\. Use this parameter to avoid overfitting the model\. Valid values: float, range: Positive floating point number\. Default value: `1.0`\.  | 
| max\_leaves |  The maximum number of leaves in the resulting tree\. Can only be used with the `"Lossguide"` growing policy\. Valid values: integer, range: \[`2`, `64`\]\. Default value: `31`\.  | 
| rsm |  Random subspace method\. The percentage of features to use at each split selection, when features are selected over again at random\. Valid values: float, range: \(`0.0`, `1.0`\]\. Default value: `1.0`\.  | 
| sampling\_frequency |  Frequency to sample weights and objects when building trees\. Valid values: string, either: \(`"PerTreeLevel"` or `"PerTree"`\)\. Default value: `"PerTreeLevel"`\.  | 
| min\_data\_in\_leaf |  The minimum number of training samples in a leaf\. CatBoost does not search for new splits in leaves with a sample count less than the specified value\. Can only be used with the `"Lossguide"` and `"Depthwise"` growing policies\. Valid values: integer, range: \(`1` or `∞`\)\. Default value: `1`\.  | 
| bagging\_temperature |  Defines the settings of the Bayesian bootstrap\. Use the Bayesian bootstrap to assign random weights to objects\. If `bagging_temperature` is set to `1.0`, then the weights are sampled from an exponential distribution\. If `bagging_temperature` is set to `0.0`, then all weights are 1\.0\. Valid values: float, range: Non\-negative float\. Default value: `1.0`\.  | 
| boosting\_type |  The boosting scheme\. "Auto" means that the `boosting_type` is selected based on processing unit type, the number of objects in the training dataset, and the selected learning mode\. Valid values: string, any of the following: \(`"Auto"`, `"Ordered"`, `"Plain"`\)\. Default value: `"Auto"`\.  | 
| scale\_pos\_weight |  The weight for positive class in binary classification\. The value is used as a multiplier for the weights of objects from positive class\. Valid values: float, range: Positive float\. Default value: `1.0`\.  | 
| max\_bin |  The number of splits for numerical features\. `"Auto"` means that `max_bin` is selected based on the processing unit type and other parameters\. For details, see the CatBoost documentation\. Valid values: string, either: \(`"Auto"` or string of integer from `"1"` to `"65535"` inclusively\)\. Default value: `"Auto"`\.  | 
| grow\_policy |  The tree growing policy\. Defines how to perform greedy tree construction\. Valid values: string, any of the following: \(`"SymmetricTree"`, `"Depthwise"`, or `"Lossguide"`\)\. Default value: `"SymmetricTree"`\.  | 
| random\_seed |  The random seed used for training\. Valid values: integer, range: Non\-negative integer\. Default value: `1.0`\. | 
| thread\_count |  The number of threads to use during the training\. If `thread_count` is `-1`, then the number of threads is equal to the number of processor cores\. `thread_count` cannot be `0`\. Valid values: integer, either: \(`-1` or positive integer\)\. Default value: `-1`\.  | 
| verbose |  The verbosity of print messages, with higher levels corresponding to more detailed print statements\. Valid values: integer, range: Positive integer\. Default value: `1`\.  | 