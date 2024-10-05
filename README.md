# GAN Project Documentation

## Table of Contents
1. [Project Overview](#project-overview)
2. [Objectives](#objectives)
3. [Dataset Description](#dataset-description)
4. [Methodology](#methodology)
   - [Data Preprocessing](#data-preprocessing)
   - [Model Architecture](#model-architecture)
   - [Training Procedure](#training-procedure)
5. [Results and Evaluation](#results-and-evaluation)
   - [Loss Curves](#loss-curves)
   - [Histograms](#histograms)
6. [Conclusion](#conclusion)
7. [Future Work](#future-work)

## Project Overview
This project implements a Generative Adversarial Network (GAN) to generate synthetic data that mimics the characteristics of a given dataset. The goal is to train a generator model to create realistic samples while a discriminator model learns to distinguish between real and generated samples.

## Objectives
- To build a GAN capable of generating synthetic data resembling the distribution of the input dataset.
- To evaluate the quality of generated samples through statistical analysis and visualization.
- To optimize the training process and model performance through various techniques.

## Dataset Description
The dataset used in this project is sourced from a CSV file containing sales data with features such as:
- **CUSTOMERNAME**: Name of the customer.
- **COUNTRY**: The country where the customer is located.
- **DEALSIZE**: Size of the deal, indicating its value.

The dataset includes categorical variables that require encoding and normalization before training the GAN.

## Methodology

### Data Preprocessing
1. **Loading the Dataset**: The dataset is loaded using Pandas.
2. **Encoding Categorical Features**: Categorical variables are converted to numerical values using Label Encoding to prepare them for training.
3. **Normalization**: The numerical values are normalized to the range [0, 1] using Min-Max Scaling for stable GAN training.
4. **Train-Test Split**: The normalized data is split into training and testing sets using an 80-20 ratio.

### Model Architecture
The GAN consists of two neural networks: the Generator and the Discriminator.

#### Generator
- The generator takes random noise as input and generates synthetic samples.
- It is composed of several dense layers with LeakyReLU activations and Batch Normalization.

**Visual: Generator Architecture**
![Generator Architecture](path/to/generator_architecture.png)

#### Discriminator
- The discriminator takes samples (real or generated) and predicts whether they are real or fake.
- It consists of dense layers with LeakyReLU activations and outputs a single probability (using a sigmoid activation function).

**Visual: Discriminator Architecture**
![Discriminator Architecture](path/to/discriminator_architecture.png)

### Training Procedure
1. **Compilation**: Both the generator and discriminator are compiled with the Adam optimizer and binary cross-entropy loss.
2. **Training Loop**:
   - For each epoch:
     - **Train the Discriminator**: Real and fake samples are used to train the discriminator.
     - **Train the Generator**: The generator is trained to improve its ability to fool the discriminator.
     - Losses are recorded for both models for further analysis.

## Results and Evaluation

### Loss Curves
- After training, the losses of both the generator and discriminator are plotted against epochs. This visualization helps to understand the dynamics of the training process and the balance between the two models.

**Visual: Loss Curves**
![Loss Curves](path/to/loss_curves.png)

### Histograms
- Histograms are plotted to compare the distribution of the generated samples with that of the real data. Key aspects analyzed include:
  - Distribution shape: Similarities and differences between real and generated distributions.
  - Range and spread: Assessing how well the generator captures the diversity of real samples.
  - Overlapping regions: Quantifying the overlap between the two distributions.

**Visual: Histogram Comparison**
![Histogram Comparison](path/to/histogram_comparison.png)

## Conclusion
The GAN was successfully implemented and trained, showing promising results in generating synthetic data. However, the performance varied across different features, with some aspects requiring further refinement.
