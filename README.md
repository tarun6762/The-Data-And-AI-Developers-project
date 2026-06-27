# The-Data-And-AI-Developers-project
An advanced AI recruitment engine using dual-model semantic scoring (retrieval + reranking) to evaluate candidates. It mathematically blends contextual fit with tiered skill density, seniority signals, and log-scaled experience. Built for production, it features Explainable AI (XAI) to provide clear, deterministic reasoning for all rankings.


#           ADVANCED CANDIDATE DISCOVERY ENGINE v2.0                
#   Multi-Factor AI Recruitment with Explainability & Calibration   


## 🎯 Project Overview
An advanced AI recruitment engine using dual-model semantic scoring (retrieval + precision reranking) to evaluate candidates. It mathematically blends contextual fit with tiered skill density, seniority signals, and log-scaled experience. Built for enterprise production scale, it features Explainable AI (XAI) to provide clear, deterministic reasoning for all candidate rankings.

## 🧠 Architectural Engineering & Scoring Logic
This engine moves beyond traditional applicant tracking systems (ATS) and shallow keyword matching by utilizing a hybrid, multi-factor approach:

1. **Two-Stage Semantic Funnel:** * **Stage 1 (Retrieval):** Uses `all-mpnet-base-v2` (Bi-Encoder) for rapid dense vector search across all candidate profiles.
   * **Stage 2 (Reranking):** Uses `ms-marco-MiniLM-L-6-v2` (Cross-Encoder) to perform deep, computationally heavy semantic reranking only on the top-K candidates.
2. **Logarithmic Experience Scaling:** Applies a log-curve calculation (`log(1+x)`) to raw years of experience, accurately capturing the real-world diminishing returns of massive tenures.
3. **Tiered Skill Taxonomy:** Scores candidates deterministically based on deep skill alignment, categorizing skills into Tier-1 (Core), Tier-2 (Strong), and Tier-3 (Bonus) buckets.
4. **Seniority Mapping:** Extracts title data heuristics to evaluate leadership and responsibility signals.

### 📊 Algorithmic Weights
The final composite score is calculated using a configurable, weighted formula:
- **Bi-Encoder Semantic Fit:** 50%
- **Cross-Encoder Rerank:** 20%
- **Log-Scaled Experience:** 15%
- **Weighted Skill Density:** 10%
- **Title Seniority Signal:** 5%

---

## 🛠️ Installation & Setup

### Prerequisites
Ensure you have Python 3.8+ installed on your machine. 

### 1. Install Dependencies
Install the required machine learning and data processing libraries:
```bash
pip install pandas numpy sentence-transformers scikit-learn openpyxl
