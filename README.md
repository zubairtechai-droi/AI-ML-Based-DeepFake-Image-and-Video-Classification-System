# AI-ML-Based-DeepFake-Image-and-Video-Classification-System
This Repository Contains link to my thesis for Image and video classification using AI/ML Based.  
Thesis contains code and result as well conduced by me.


# Deep Authenticator: Compressed DeepFake Detection

**Deep learning · Computer Vision · Digital Media Forensics · TensorFlow * Machine Learning**

A two-stream convolutional neural network (CNN) that detects DeepFake videos even after heavy compression, the condition under which most social media videos are shared and under which most detectors fail.

> Master's thesis, Computer Science, University of New Brunswick (Canadian Institute for Cybersecurity). Supervisor: Dr. Saqib Hakak.

## Problem

Generative AI has made realistic DeepFakes easy to produce, and social media platforms compress video heavily to save storage and bandwidth. Compression destroys the subtle artifacts that most detectors rely on, so accuracy drops sharply on real-world, low-quality video. Deep Authenticator is built for that setting.

## Approach

| Component | Description |
|---|---|
| **I-Frame extraction** | Uses the H.264 video structure (FFmpeg) and keeps only I-Frames, which are decoded independently of other frames. This keeps inference efficient and scalable. |
| **Face detection & preprocessing** | dlib face detection, cropping, resizing and data augmentation. |
| **RGB stream** | A fine-tuned CNN backbone (EfficientNet-B4/B7, ResNet-152, Xception, VGG-19, MesoNet compared) that learns semantic inconsistencies. |
| **Noise (residual) stream** | Spatial Rich Model (SRM) high-pass filters feeding a CNN to capture noise-level forgery traces. Using more than 3 SRM filters (9 and 27 tested) improved detection. |
| **Fusion / ensemble** | Late fusion of the RGB and SRM streams with a tuned weighting. |
| **Explainability** | Grad-CAM visualizations showing which facial regions drive predictions. |

## Results

- Evaluated on **FaceForensics++** (DeepFakes, Face2Face, FaceSwap, NeuralTextures), **Celeb-DF-V1** and **Celeb-DF-V2**
- Tested at two compression levels (**C23 high quality, C40 low quality**)
- Reported accuracy, precision, recall and F1: **[insert best accuracy / F1 here]**
- Compared against PRNU, HFXception and a dual-stream spatio-temporal method, with strong results across datasets while using fewer frames per video
- The ensemble outperformed each single-stream baseline

## Key Contributions

1. A dual-stream architecture combining semantic (RGB) and noise-residual (SRM) features for compressed video
2. An ablation study on the number of SRM filters (3 vs 9 vs 27) across three backbones
3. A new classification taxonomy of DeepFake types, plus a literature survey of compression-aware and compression-centric detection methods
4. Cross-dataset, multi-compression evaluation with interpretability analysis

## Tech Stack

`Python` · `TensorFlow 2.x` · `Keras` · `OpenCV` · `FFmpeg` · `dlib` · `NumPy` · `scikit-learn` · `Google Colab (NVIDIA L4 GPU)` · `LaTeX`

## Topics

DeepFake detection, video forensics, media authentication, synthetic media detection, convolutional neural networks, transfer learning, image forensics, SRM filters, noise residual analysis, ensemble learning, model interpretability (Grad-CAM), video compression (H.264), generative AI safety, trustworthy AI, misinformation detection, cybersecurity, GANs, diffusion models, autoencoders, FaceForensics++, Celeb-DF

## Repository Structure

```
├── preprocessing/   # H.264 compression, I-Frame extraction, face detection
├── models/          # RGB stream, SRM layer, fusion model
├── training/        # training and evaluation scripts
├── notebooks/       # experiments and Grad-CAM visualizations
└── thesis/          # full thesis PDF
```

## Usage

```bash
git clone https://github.com/<your-username>/deep-authenticator
cd deep-authenticator
pip install -r requirements.txt
python preprocessing/extract_iframes.py --input <videos> --output <frames>
python training/train_rgb.py --backbone resnet152
python training/train_srm.py --filters 9
python training/evaluate_ensemble.py
```

## Citation

```
Zubair, M. (2025). Deep Authenticator: A Method for Compressed DeepFake Detection.
Master's Thesis, University of New Brunswick.
```

## Contact



# Link to Final Document

https://unbscholar.lib.unb.ca/items/62776778-2d54-4704-addb-c63d1adfa96e
