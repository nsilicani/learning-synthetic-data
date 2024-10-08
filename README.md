# Learning Synthetic Data Generation

This project focuses on synthetic data generation techniques across two key domains: Credit and Insurance. The goal is to create high-quality synthetic datasets that can be used for various purposes, including machine learning model training.

## Table of Contents
- [Introduction](#introduction)
- [Installation](#installation)
- [Usage](#usage)
- [Credit Domain](#credit-domain)
  - [Overview](#overview)
  - [Data Generation Techniques](#data-generation-techniques)
- [Insurance Domain](#insurance-domain)
  - [Overview](#overview)
- [Conclusion](#conclusion)
- [Contributing](#contributing)

## Introduction
Synthetic data generation is a powerful tool that allows the creation of artificial datasets that retain the statistical properties of real-world data while preserving privacy and enabling the testing of models and algorithms. This project explores synthetic data generation in the domains of credit and insurance.

## Usage
This is an educational project. Code is organized in notebooks. To download the dataset, please export the following environmental variables in the `.env`, located at the root of the project:
```bash
KAGGLE_USERNAME=<Kaggle Username>
KAGGLE_KEY=<Kaggle API Key>
```

## Credit Domain
### Overview
In the credit domain, synthetic data is generated to simulate various credit scenarios. This includes data related to credit scoring, loan applications, and customer credit behavior. In the credit scoring context, a common problem is the class imbalance (i.e. the instances of default individuals are only a minority percentage compared to _in bonis_ positions in the dataset). In the analyzed dataset, the three classes, correspondig to _Poor_, _Standard_ and _Good_ creditworthiness respectively, present such imbalance: $Poor = 29\%$, $Standard = 53\%$ and $Good = 18\%$. The project's goal is to generate syntethic data for such use case, in order to mitigate the class imbalance. \
We use the Kaggle dataset [`parisrohan/credit-score-classification`](https://www.kaggle.com/datasets/parisrohan/credit-score-classification).

### Data Generation Techinques
The techniques used in the credit domain include:

- **GANs (Generative Adversarial Networks)**: Used to generate realistic credit profiles and transaction histories.
- **Variational Autoencoders (VAEs)**: Employed to create diverse synthetic datasets that retain the statistical properties of the original data.
- **Random Sampling and Perturbation**: Simple yet effective methods to create variations in the data while preserving key characteristics.

In this project we use GANs.

## Insurance Domain
### Overview
In the insurance domain, synthetic data is generated to replicate various insurance-related scenarios, including policyholder data, claim records, and risk profiles. The aim is to create synthetic datasets that are useful for testing, research, and model training without exposing real-world data. \ 
We use the Kaggle dataset [annantkumarsingh/health-insurance-cross-sell-prediction-data](https://www.kaggle.com/datasets/anmolkumar/health-insurance-cross-sell-prediction).
In this educational example, we consider an upselling context. The analyzed dataset present these class relationship: $class_{0} = 88\% $ and $class_{1} = 12\%$. In particular, we want to augment the dimensionality of our dataset with respect the response class 1, i.e. policyholders from past year that will also be interested in Vehicle Insurance provided by the company.

## Conclusion
The empirical results reveal a common challenge in synthetic data generation: model collapse. This occurs when both models, particularly the Generator, tend to focus on generating specific values repeatedly, rather than accurately learning and replicating the full distribution of input features. To mitigate this issue, potential strategies include:

- Introducing Regularization Techniques: Applying regularization can prevent overfitting and encourage the model to explore a broader range of the data distribution.
- Adjusting Model Architecture: Experimenting with different architectures, such as deeper networks or modified loss functions, can help improve the Generator's ability to capture the complexity of the input data. Other architectures to explore are:
    - Conditional GANs (cGANs): Conditional GANs extend the basic GAN architecture by conditioning both the Generator and the Discriminator on additional information, such as class labels or specific features. This allows the model to generate data that adheres to certain conditions, leading to more controlled and diverse outputs
    - Wasserstein GAN (WGAN): WGANs modify the loss function of the GAN by using the Wasserstein distance instead of the Jensen-Shannon divergence. This approach provides a more stable training process and helps mitigate issues like mode collapse
    - Deep Convolutional GAN (DCGAN): DCGANs use convolutional neural networks (CNNs) in both the Generator and the Discriminator. The convolutional layers help the model capture spatial hierarchies in the data, making it particularly effective for image-like data but also applicable to structured data with some adaptations
    - Variational Autoencoder GAN (VAE-GAN): VAE-GAN combines the strengths of Variational Autoencoders (VAEs) and GANs. The VAE is used to generate latent variables that are then fed into a GAN, which generates the final synthetic data. This architecture benefits from the generative capabilities of VAEs while maintaining the realistic output of GANs
- Incorporating Diversity Promoting Constraints: Adding constraints or penalties that encourage the Generator to produce more diverse outputs can help prevent mode collapse.
- Increasing Training Data: Using a larger and more diverse training dataset can provide the model with more varied examples, aiding in learning a more comprehensive distribution.

By applying these strategies, the synthetic data generation process can be improved, leading to more accurate and representative synthetic datasets in both the credit and insurance domains. Further research and experimentation will be necessary to refine these techniques and overcome the challenges inherent in generating high-quality synthetic data.



## Contributing
Contributions to this project are welcome! Please fork the repository and submit a pull request with your changes. Ensure your code adheres to the project's coding standards and is well-documented.

