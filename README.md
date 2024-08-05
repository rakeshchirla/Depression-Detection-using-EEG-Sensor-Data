# Depression Detection using EEG Sensor Data

This repository contains the code and documentation for the project "Depression Detection using EEG," aimed at leveraging deep learning techniques for the automated estimation of depression using EEG data.

## Table of Contents
- [Introduction](#introduction)
- [Dataset](#dataset)
- [Preprocessing](#preprocessing)
- [Models](#models)
- [Results](#results)
- [Challenges](#challenges)
- [Future Work](#future-work)

## Introduction
Mental health disorders such as depression and anxiety affect millions of people worldwide. Traditional diagnostic methods often fall short in effectively detecting these conditions. This project utilizes EEG sensors to gain insights into cognitive and emotional states through brain wave patterns. By applying deep learning techniques, we aim to develop an Automated Depression Estimation system for accurate and early detection of depression.

## Dataset
We utilized the MODMA dataset, comprising:
- **Subjects**: 53 total
  - Major Depressive Disorder: 24
  - Healthy Control: 29

### Data Collection Procedure
- **Setup**: 128 electrodes
- **Trials**: 160 per participant
- **Procedure**: 
  - Fixed white cross displayed for 300 ms
  - Emotional-neutral face pair cue for 500 ms
  - Dot-probe target appears left or right of the cross for 150 ms
  - Participants identify dot location and respond using buttons
  - Automatic 2000 ms interval for response followed by the next trial

### Data Access
Access to the MODMA dataset required authorization via a signed license agreement.

## Preprocessing
1. **Conversion**: Raw EEG files (.raw) converted to CSV format using EEGLab.
2. **Segmentation**: Time-series data divided into batches of 2000 data points.
3. **Labeling**: Data labeled as 1 for depressed and 0 for non-depressed.
4. **Filtering**: Applied Butterworth bandpass filter (4.0-13.0 Hz) and notch filter (50.0 Hz) to remove noise.
5. **Augmentation**: Utilized sliding windows to enhance data richness.

## Models
We explored multiple models, both 1D and 2D Convolutional Neural Networks (CNNs), and specific architectures for EEG data such as EEGNet and EEGConformer.

### Baseline Models
- **ResNet 1D**: 52.05%
- **ResNet 2D**: 57.06%
- **VGG 16 1D**: 51.24%
- **VGG 16 2D**: 56.00%
- **VGG 19 1D**: 51.40%
- **VGG 19 2D**: 59.33%

### Advanced Models
- **CNN + LSTM**: 64.56%
- **LSTM**: 62.86%
- **EEGNet**: 63.11%
- **EEGConformer**: 63.45%
- **ResNet (Images)**: 65.74%

## Results
The best results were achieved using the ResNet50 model with image generation from EEG signal plots, achieving a validation accuracy of 65.74%.

## Challenges
- **Data Availability**: Limited data availability and proprietary access issues.
- **Data Preprocessing**: Challenges in extracting and processing data from MATLAB files.
- **Overfitting**: Overfitting due to limited data, addressed through augmentation and various preprocessing techniques.

## Future Work
- Experiment with advanced data augmentation techniques like time-warping, spectral augmentation, and adding noise.
- Incorporate additional data sources such as facial expressions and physiological signals.
- Explore transfer learning with pre-trained models on larger EEG datasets.
- Validate model performance on clinically diagnosed depression populations.
