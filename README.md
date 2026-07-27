# CineAI

> An intelligent **Hybrid Movie Recommendation System** that combines Collaborative Filtering, Content-Based Recommendation, Popularity Modeling, and Feature Engineering into a unified recommendation pipeline.

![Python](https://img.shields.io/badge/Python-3.11-blue)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-ML-orange)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Processing-lightgrey)
![NumPy](https://img.shields.io/badge/NumPy-Scientific%20Computing-blue)
![Status](https://img.shields.io/badge/Status-Active%20Development-success)

---
# CineAI

A **two-stage hybrid movie recommendation system** that combines collaborative filtering, content-based retrieval, popularity modeling, and feature-based ranking to generate personalized movie recommendations.

CineAI is built using the **MovieLens 32M** dataset and follows a modular recommendation architecture inspired by modern large-scale recommender systems. The project emphasizes reproducible experimentation, leakage-free evaluation, and extensible system design.

---

## Overview

Most recommendation systems rely on a single recommendation strategy, making them susceptible to issues such as cold-start users, sparsity, or overspecialized recommendations.

CineAI addresses these challenges by adopting a **two-stage recommendation pipeline**:

- **Stage 1:** Retrieve relevant candidate movies using multiple recommendation engines.
- **Stage 2:** Rank the retrieved candidates using engineered recommendation features.

This separation enables each stage to evolve independently and mirrors the architecture used in production recommendation systems.

---

## System Architecture

```

                          MovieLens 32M
                                │
                                ▼
                     Feature Engineering
                                │
                                ▼
══════════════════════════════════════════════════════
           Stage 1 : Candidate Generation
══════════════════════════════════════════════════════

     Collaborative Filtering (Truncated SVD)
                     │

        Content-Based Retrieval (TF-IDF)
                     │

      Popularity-Based Recommendation
                     │
                     ▼

          Unified Candidate Pool

══════════════════════════════════════════════════════
             Stage 2 : Candidate Ranking
══════════════════════════════════════════════════════

For every candidate movie:

• Collaborative Score
• Content Similarity Score
• Genre Preference Score
• Popularity Score
• Average Rating
• Rating Count
• Recency Score

                     │
                     ▼

        Feature-Based Hybrid Ranking

                     │
                     ▼

     Personalized Top-K Recommendations

```

---

## Features

### Two-Stage Recommendation Architecture

Instead of directly recommending movies from a single model, CineAI first retrieves candidate movies and subsequently ranks them using multiple recommendation signals.

---

### Collaborative Filtering

- Matrix Factorization
- Truncated Singular Value Decomposition (SVD)
- Captures latent user-item interactions

---

### Content-Based Retrieval

- TF-IDF movie representation
- Cosine similarity search
- Content-aware recommendations

---

### Popularity Modeling

Popularity candidates are generated using IMDb weighted ratings instead of simple averages to reduce bias toward movies with few interactions.

---

### Personalized Genre Modeling

User-specific genre preferences are estimated from historical interactions and incorporated into the final ranking stage.

---

### Hybrid Feature-Based Ranking

Each recommendation candidate is represented using multiple engineered features.

| Feature | Description |
|----------|-------------|
| Collaborative Score | Latent user preference |
| Content Score | Content similarity |
| Genre Preference Score | User affinity toward movie genres |
| Average Rating | Historical movie quality |
| Rating Count | Confidence estimate |
| Popularity Score | Global popularity |
| Recency Score | Preference toward recent movies |

The ranking engine combines these features to generate the final recommendation list.

---

### Cold-Start Recommendation

Users with limited interaction history are handled using popularity-based recommendations generated through IMDb weighted ratings.

---

## Recommendation Pipeline

1. Dataset preprocessing
2. Feature engineering
3. Train / Validation / Test split
4. Collaborative candidate generation
5. Content candidate generation
6. Popularity candidate generation
7. Candidate merging
8. Feature construction
9. Hybrid ranking
10. Top-K recommendation generation
11. Offline evaluation

---

## Evaluation

The project follows a leakage-free evaluation protocol.

Training interactions are used exclusively for model construction.

Validation interactions are reserved for model tuning.

Testing interactions are used only for final offline evaluation.

### Current Evaluation Metrics

| Metric |
|---------|
| Precision@K |
| Recall@K |
| MAP@K |
| NDCG@K |
| Coverage |
| Latency |
| Novelty |
| Diversity |
| Hit Rate@K |

---

## Dataset

MovieLens 32M

- 32 Million Ratings
- 2 Million Tag Applications

---

## Technology Stack

### Machine Learning

- Scikit-learn
- NumPy
- Pandas
- SciPy

### Recommendation Algorithms

- Truncated SVD
- TF-IDF
- Cosine Similarity

### Engineering

- Sparse Matrix Operations
- Joblib Serialization
- Modular Pipeline Design

---


---

## Engineering Highlights

- Two-stage recommendation architecture
- Hybrid recommendation pipeline
- Leakage-free evaluation protocol
- Modular candidate generation
- Feature-based ranking
- Cold-start recommendation strategy
- Sparse matrix optimization
- Artifact serialization for reproducibility

---

## Current Status

Implemented

- Feature Engineering
- Content-Based Recommendation
- Collaborative Filtering
- Popularity Recommendation
- Two-Stage Hybrid Recommendation
- Cold-Start Recommendation
- Offline Evaluation Framework

Planned

- Learning-to-Rank (XGBoost / LightGBM)
- Explainable Recommendations
- ANN Retrieval (FAISS)
- FastAPI Deployment
- Docker Support

---

## Future Work

Future improvements include:

- Learning-to-Rank for candidate ranking
- Explainable recommendation generation
- Approximate nearest-neighbor retrieval
- Real-time recommendation service
- Online A/B evaluation
- User feedback incorporation

---
