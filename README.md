# Optimizing Delivery ETAs with Graph-Based Network Intelligence

Graph analytics and machine learning framework for **ETA optimization, bottleneck detection, route intelligence, and shipment mode classification** in large-scale logistics networks.

![Python](https://img.shields.io/badge/Python-3.x-blue)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-green)
![Graph Analytics](https://img.shields.io/badge/Graph-Analytics-orange)

---

## Overview

Large logistics networks often experience cascading delays, where congestion at a few critical hubs impacts hundreds of downstream shipments.

This project models the logistics network as a **directed graph** and combines **graph analytics with machine learning** to:

* Detect bottleneck hubs causing major delays
* Identify chronically delayed transport corridors
* Improve shipment ETA prediction
* Build a **route-type decision framework (FTL vs Carting)**
* Generate actionable operational insights

The goal is not just to predict delays, but to understand **why delays happen and where intervention matters most**.

---

## Dataset

* **1,240 facilities (nodes)**
* **1,635 transport corridors (edges)**

### Features Used

* Source / Destination facility
* Route type (**FTL / Carting**)
* Time of day
* Actual trip duration
* OSRM estimated travel time
* Delay ratio
* Corridor traffic statistics
* Graph centrality measures
* Node embeddings

---

## Methodology

### 1. Data Preprocessing

* Removed missing and invalid records
* Cleaned inconsistent route labels
* Standardized time windows
* Aggregated corridor-level statistics

### 2. Graph Modeling

The logistics network was modeled as a **directed graph**:

* **Nodes** → Facilities
* **Edges** → Transport corridors

Extracted graph-based features:

* Betweenness centrality
* In-degree / Out-degree
* Flow balance
* Node2Vec embeddings

### 3. Route-Type Classification (FTL vs Carting)

A classification model was built to recommend the optimal shipment mode:

* **FTL (Full Truck Load)**
* **Carting**

This framework improves:

* Delivery efficiency
* Vehicle utilization
* Routing costs
* ETA reliability

### 4. ETA Prediction

Two regression models were built:

#### Baseline Model

Uses conventional shipment features.

#### Graph-Enhanced Model

Uses:

* Graph centrality features
* Corridor statistics
* Node embeddings

This enables the model to learn structural delay propagation across the network.

---

## Results

### Route-Type Classifier Performance

| Metric   |   Score |
| -------- | ------: |
| Accuracy | **96%** |

The classifier reliably determines whether a shipment should use **FTL or Carting**, enabling smarter routing decisions.

---

### ETA Prediction Performance

| Metric       | Baseline | Graph-Enhanced |
| ------------ | -------: | -------------: |
| MAE          | 17.3 min |   **14.0 min** |
| ETA Accuracy |    24.7% |      **34.3%** |

### Key Improvements

* **~19% reduction in MAE**
* **+9.6 percentage point improvement in ETA accuracy**

---

## Key Insights

* Delays are concentrated around a few critical hubs
* Evening **FTL routes** are the most delay-prone
* Bottlenecks create cascading downstream delays
* Top 3 hubs contribute **34.6% of total delay minutes**

### Business Impact

The graph-enhanced model’s ability to anticipate structural bottlenecks provides a direct pathway to:

* Reducing **SLA breaches** through earlier delay detection
* Improving **shipment reliability** across critical corridors
* Enabling proactive hub-level interventions before delays cascade
* Recovering potentially **at-risk operational revenue** caused by delayed deliveries

By improving ETA prediction and route planning, the system enables logistics teams to make faster and more cost-effective operational decisions.

---

## Tech Stack

* Python
* pandas
* numpy
* scikit-learn
* networkx
* matplotlib
* seaborn
* node2vec
* Jupyter Notebook

---

## Repository Structure

```bash
.
├── PS4_Delivery_ETA_Submission/
│   ├── ETA_Optimization.ipynb
│   ├── Network Operations Strategy Memo.pdf
│   └── images/
│       ├── model benchmarks.jpeg
│       └── network bottlenecks.jpeg
└── README.md
```

---

### Visualizations

**Network Bottlenecks**
![Network Bottlenecks Diagram](images/network_bottlenecks.jpeg)

**Model Benchmarks**
![Model Benchmarks Chart](images/model_benchmarks.jpeg)

---

## Installation

```bash
git clone <repository-url>
cd <repository-folder>
pip install -r requirements.txt
```

Run notebook:

```bash
jupyter notebook
```

---

## Future Work

* Graph Neural Networks (GNNs)
* Real-time traffic and weather integration
* Live ETA monitoring dashboards
* Periodic model retraining

---

## Contributors

* **Rutuja Shyamrao Kabadi**
* **Wagh Unmesh Pradeep**

Built as part of a **Summer Project**, exploring how graph intelligence and machine learning can improve logistics efficiency and delivery reliability.
