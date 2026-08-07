<div id="top"></div>

<br>

<p align="center">
  <a href="https://github.com/soph-k">
    <img
      src="https://img.shields.io/badge/Made%20by-soph--k-d9a07e?style=for-the-badge&amp;labelColor=123b3d"
      alt="Made by soph-k"
    />
  </a>
  <a href="https://www.python.org/">
    <img
      src="https://img.shields.io/badge/Python-123b3d?style=for-the-badge&amp;logo=python&amp;logoColor=fffaf4"
      alt="Python"
    />
  </a>
  <a href="https://www.tensorflow.org/">
    <img
      src="https://img.shields.io/badge/TensorFlow-d9a07e?style=for-the-badge&amp;logo=tensorflow&amp;logoColor=123b3d"
      alt="TensorFlow"
    />
  </a>
  <a href="https://pytorch.org/">
    <img
      src="https://img.shields.io/badge/PyTorch-123b3d?style=for-the-badge&amp;logo=pytorch&amp;logoColor=fffaf4"
      alt="PyTorch"
    />
  </a>
</p>

<br>

<div align="center">

<a href="https://github.com/soph-k">
  <img
    src="https://raw.githubusercontent.com/soph-k/logo/main/logo.png"
    width="95"
    alt="soph-k logo"
  />
</a>

<h2>『 Deep Learning Crop Recommendation 』</h2>

<p>
  A multiclass deep-learning project that recommends crops using soil nutrients,
  temperature, humidity, pH, and rainfall.
</p>

<p>────── ♡ ──────</p>

<p>
  <a href="./final_2.ipynb">
    <strong>View Notebook »</strong>
  </a>
  &nbsp; • &nbsp;
  <a href="https://colab.research.google.com/github/soph-k/crop-recommendation-deep-learning/blob/main/final_2.ipynb">
    <strong>Open in Colab »</strong>
  </a>
</p>

</div>

<br>

<p align="center">
  <img
    src="https://img.shields.io/badge/Cross--Validation-98.01%25-d9a07e?style=for-the-badge&amp;labelColor=123b3d"
    alt="98.01 percent cross-validation accuracy"
  />
  <img
    src="https://img.shields.io/badge/TensorFlow%20Test-97.03%25-d9a07e?style=for-the-badge&amp;labelColor=123b3d"
    alt="97.03 percent TensorFlow test accuracy"
  />
  <img
    src="https://img.shields.io/badge/PyTorch%20Test-97.95%25-d9a07e?style=for-the-badge&amp;labelColor=123b3d"
    alt="97.95 percent PyTorch test accuracy"
  />
</p>

<p align="center">
  <sub>Precision agriculture • Neural networks • Explainable machine learning</sub>
</p>

<br>

## ❐ About the Project

Crop suitability depends on the relationship between soil composition and
environmental conditions. This project develops neural-network models that learn
those relationships and classify the most suitable crop for a given agricultural
profile.

The models use seven original inputs:

```text
Nitrogen • Phosphorus • Potassium • Temperature • Humidity • pH • Rainfall
```

The notebook covers the full workflow from exploratory analysis and preprocessing
to model training, evaluation, ensembling, and interpretation.

> **Project goal:** build an accurate and interpretable crop-recommendation
> pipeline using structured soil and climate data.

<p align="right">(<a href="#top">back to top</a>)</p>

<br>

## ❐ Project at a Glance

| Category | Details |
|---|---|
| Original dataset | `2,200 observations` |
| Base inputs | `7 soil and environmental features` |
| Engineered inputs | `17 total model features` |
| Retained crop classes | `20` |
| Primary model | TensorFlow neural-network ensemble |
| Comparison model | PyTorch multilayer perceptron |
| Interpretation | Permutation importance and Integrated Gradients |

### Main Features

- Exploratory data analysis and visualization
- Missing-value and outlier analysis
- Feature scaling and crop-label encoding
- Nutrient-ratio and climate-interaction features
- Stratified three-fold cross-validation
- Early stopping and learning-rate reduction
- Ensemble probability averaging
- Independent PyTorch model comparison
- Global and individual prediction explanations

<p align="right">(<a href="#top">back to top</a>)</p>

<br>

## ❐ Workflow

```mermaid
flowchart LR
    A["Crop Dataset"] --> B["Clean + Explore"]
    B --> C["Engineer Features"]
    C --> D["Scale + Encode"]
    D --> E["Train Models"]
    E --> F["Evaluate"]
    F --> G["Explain Predictions"]

    classDef teal fill:#123b3d,stroke:#d9a07e,color:#fffaf4,stroke-width:2px;
    classDef cream fill:#f7efe7,stroke:#d9a07e,color:#123b3d,stroke-width:2px;
    classDef rose fill:#d9a07e,stroke:#123b3d,color:#123b3d,stroke-width:2px;

    class A,B teal;
    class C,D cream;
    class E,F,G rose;

    linkStyle default stroke:#d9a07e,stroke-width:2px;
```

### Feature Engineering

The seven original variables are expanded with several relationship-based features:

```text
N/P ratio
N/K ratio
P/K ratio
Total NPK
Temperature-humidity interaction
pH category indicators
```

These additions allow the model to learn interactions that may not be represented
by the original measurements individually.

<p align="right">(<a href="#top">back to top</a>)</p>

<br>

## ❐ Models and Results

### TensorFlow Ensemble

The primary workflow trains three regularized neural networks using stratified
cross-validation. Their probability outputs are averaged to produce the final
ensemble prediction.

Training includes:

- Dense neural-network layers
- Batch normalization
- Gaussian noise
- Dropout
- L1 and L2 regularization
- Early stopping
- Adaptive learning-rate reduction

### PyTorch MLP

A separate PyTorch multilayer perceptron is trained as an independent comparison
using the original scaled features.

| Model | Evaluation | Accuracy |
|---|---|---:|
| TensorFlow ensemble | Three-fold cross-validation mean | **98.01%** |
| TensorFlow ensemble | Cross-validation variation | **± 0.34%** |
| TensorFlow ensemble | Held-out test data | **97.03%** |
| PyTorch MLP | Held-out test data | **97.95%** |

Both implementations classified crops with approximately 97–98% accuracy. The
TensorFlow workflow provides stronger regularization and ensemble evaluation,
while the PyTorch model offers a simpler independent comparison.

<p align="right">(<a href="#top">back to top</a>)</p>

<br>

## ❐ Model Interpretation

Permutation importance measures how much model performance decreases when a
feature is randomly shuffled.

| Rank | Feature | Importance |
|---:|---|---:|
| 1 | Rainfall | `0.2683` |
| 2 | Humidity | `0.1789` |
| 3 | Potassium | `0.1357` |
| 4 | Temperature-humidity interaction | `0.1201` |
| 5 | Phosphorus | `0.1169` |

Rainfall and humidity were the strongest global predictors, followed by soil
nutrients and the engineered temperature-humidity interaction.

Integrated Gradients is also used to explain individual recommendations by
showing which inputs contributed positively or negatively to the predicted crop.

<p align="right">(<a href="#top">back to top</a>)</p>

<br>

## ❐ Built With

<p align="center">
  <img
    src="https://img.shields.io/badge/Python-123b3d?style=for-the-badge&amp;logo=python&amp;logoColor=fffaf4"
    alt="Python"
  />
  <img
    src="https://img.shields.io/badge/TensorFlow-d9a07e?style=for-the-badge&amp;logo=tensorflow&amp;logoColor=123b3d"
    alt="TensorFlow"
  />
  <img
    src="https://img.shields.io/badge/PyTorch-123b3d?style=for-the-badge&amp;logo=pytorch&amp;logoColor=fffaf4"
    alt="PyTorch"
  />
  <img
    src="https://img.shields.io/badge/scikit--learn-d9a07e?style=for-the-badge&amp;logo=scikitlearn&amp;logoColor=123b3d"
    alt="scikit-learn"
  />
</p>

<p align="center">
  <img
    src="https://img.shields.io/badge/pandas-123b3d?style=for-the-badge&amp;logo=pandas&amp;logoColor=fffaf4"
    alt="pandas"
  />
  <img
    src="https://img.shields.io/badge/NumPy-d9a07e?style=for-the-badge&amp;logo=numpy&amp;logoColor=123b3d"
    alt="NumPy"
  />
  <img
    src="https://img.shields.io/badge/Matplotlib-123b3d?style=for-the-badge"
    alt="Matplotlib"
  />
  <img
    src="https://img.shields.io/badge/Seaborn-d9a07e?style=for-the-badge"
    alt="Seaborn"
  />
</p>

<p align="right">(<a href="#top">back to top</a>)</p>

<br>

## ❐ Repository Structure

```text
crop-recommendation-deep-learning/
├── data/
│   └── Crop_recommendation.csv
│
├── final_2.ipynb
└── README.md
```

| File | Purpose |
|---|---|
| `final_2.ipynb` | Data analysis, modeling, evaluation, and interpretation |
| `data/Crop_recommendation.csv` | Soil, climate, and crop-label dataset |
| `README.md` | Project overview and setup instructions |

<p align="right">(<a href="#top">back to top</a>)</p>

<br>

## ▹ Getting Started

Clone the repository:

```bash
git clone https://github.com/soph-k/crop-recommendation-deep-learning.git
cd crop-recommendation-deep-learning
```

Create and activate a virtual environment:

```bash
python -m venv .venv
```

Windows:

```powershell
.venv\Scripts\Activate.ps1
```

macOS or Linux:

```bash
source .venv/bin/activate
```

Install the dependencies:

```bash
pip install numpy pandas matplotlib seaborn scikit-learn tensorflow torch jupyter
```

Start Jupyter:

```bash
jupyter notebook final_2.ipynb
```

The notebook expects the dataset at:

```text
data/Crop_recommendation.csv
```

<p align="right">(<a href="#top">back to top</a>)</p>

<br>

## ❐ Limitations and Future Work

- Validate the models using data from additional regions and seasons
- Add geographic, soil-moisture, and seasonal variables
- Improve PyTorch training with early stopping and learning-rate scheduling
- Save trained models and preprocessing objects for reuse
- Return confidence scores and alternative crop recommendations
- Build a lightweight interface for entering soil measurements
- Evaluate crop yield and economic suitability alongside crop classification

<p align="right">(<a href="#top">back to top</a>)</p>

<br>

<div align="center">

<p>────── ♡ ──────</p>

<p><strong>Data-driven crop recommendations from soil and climate conditions</strong></p>

<sub>✦ Analyze thoughtfully ✦ Model carefully ✦ Recommend responsibly ✦</sub>

</div>

<p align="right">(<a href="#top">back to top</a>)</p>