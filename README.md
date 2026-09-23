# 3D Reconstruction and Scene Completion from SONAR Point Clouds

This project is based on my Master's thesis conducted in collaboration with the
Marine Perception research group at DFKI.

The work investigates methods for reconstructing incomplete underwater environments
from SONAR point clouds, with a particular focus on bathymetry and underwater
vegetation.

---

## 🎯 Project Motivation

SONAR point clouds are often affected by:

- Noise
- Sparsity
- Occlusions
- Missing measurements
- Irregular point distributions

These characteristics make underwater 3D reconstruction challenging.

This project investigates both **geometric reconstruction methods** and
**deep-learning-based scene completion** for recovering missing underwater geometry.

---

## 🔬 Main Objectives

- Reconstruct underwater bathymetric surfaces from SONAR point clouds
- Investigate 3D scene completion for missing and occluded regions
- Adapt LiDAR-based deep learning approaches to SONAR data
- Estimate underwater vegetation height 
- Compare geometric and learning-based reconstruction approaches

---

## 🧠 Methods

### 1. Point Cloud Preprocessing

The original SONAR point clouds were processed and divided into local regions suitable
for reconstruction and machine learning.

Processing included:

- Voxel-based processing
- Local coordinate normalization
- Generation of partial observations
- Conversion into training-compatible point-cloud representations

---

### 2. Diffusion-Based Scene Completion

A diffusion-based point-cloud completion model was investigated for reconstructing
missing 3D geometry.

The work explored:

- LiDAR-to-SONAR domain adaptation
- Transfer learning
- Fine-tuning on SONAR point clouds
- Training on SONAR data
- Synthetic experiments for evaluating learning behaviour

The experiments showed that the model could learn meaningful 3D completion patterns,
while surface-dominated bathymetric data presented challenges compared with
object-rich 3D scenes.

---

### 3. Bathymetric Reconstruction using Ordinary Kriging

Ordinary Kriging was implemented as a geometric baseline for reconstructing the
lakebed surface.

Unlike unrestricted 3D scene completion, Kriging estimates a surface elevation for
each horizontal location, making it well suited to bathymetric reconstruction.

The method achieved approximately:

**Chamfer Distance: 0.17 m**

for the evaluated bathymetric reconstruction setup.

---

### 4. Underwater Vegetation Analysis

A local bathymetric floor estimation method was developed to estimate vegetation
height above the lakebed.

The workflow included:

- Local ground / floor estimation
- Height calculation relative to the estimated bathymetric surface
- Vegetation classification based on height
- Spatial vegetation mapping

The analysis identified approximately **46.8% vegetation coverage** in the processed
survey point cloud.

---

## 📊 Evaluation

The reconstruction methods were evaluated using quantitative and qualitative analysis.

Metrics included:

- Chamfer Distance
- RMSE
- F-score

Visual inspection of reconstructed point clouds was also used to analyse geometric
quality and over-completion behaviour.

---

## 🔍 Key Findings

The experiments highlighted an important distinction between **3D scene completion**
and **bathymetric surface reconstruction**.

- Diffusion-based scene completion can generate complex 3D structures, but it may
  also over-complete regions when the input contains ambiguous elevated structures
  such as underwater vegetation.

- For predominantly smooth bathymetric surfaces, **Ordinary Kriging provided a more
  conservative and reliable reconstruction** by estimating a single surface elevation
  for each horizontal location.

- Experiments with synthetic 3D structures showed that diffusion-based models learn
  more effectively when the training data contains richer three-dimensional geometry.

- The results also demonstrated the importance of preprocessing, partial-input
  generation, and the structure of the training data when adapting LiDAR-based
  completion methods to SONAR point clouds.

## 🛠 Technologies

- Python
- PyTorch
- Open3D
- Point Cloud Library (PCL)
- NumPy
- Scikit-learn
- Matplotlib
- Linux
- Diffusion Models
- Geostatistics / Ordinary Kriging
- LiDAR Point Clouds
- SONAR Point Clouds
- Transfer Learning
- Domain Adaptation

---

## 📄 Research

This project formed the basis of my Master's thesis:

**3D Reconstruction and Scene Completion of Bathymetry and Underwater Vegetation
from SONAR Point Clouds**

The work also contributed to the research paper:

**Adapting Diffusion-Based LiDAR Scene Completion to Underwater SONAR Bathymetry**

The paper investigates the challenges of transferring learning-based point-cloud
completion methods from terrestrial LiDAR environments to underwater SONAR
bathymetry.

## 👩‍💻 Author

**Varchaswi Madamanchi**

Computer Vision & AI Engineer  
MSc Electronics Engineering – Hochschule Bremen

[LinkedIn](https://www.linkedin.com/in/varchaswi-madamanchi-7b8831177)


## 📂 Repository Structure

sonar-3d-scene-completion/
│
├── README.md
│
├── images/
│   ├── sonar_pointcloud.png
│   ├── preprocessing_pipeline.png
│   ├── kriging_result.png
│   ├── diffusion_result.png
│   └── vegetation_analysis.png
│
└── docs/
    └── paper.pdf
