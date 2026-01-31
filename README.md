# 🎯 Scouting Similar Football Players Using Machine Learning

**Solving Real-World Problems: Who Can Replace Mohamed Salah?**



## 📖 Project Overview

This project tackles a real challenge faced by Liverpool FC during the 2022 Africa Cup of Nations: finding a replacement for Mohamed Salah while he represents Egypt. Using the FIFA 22 dataset and machine learning, I built a player recommendation system that identifies the most similar players based on 30+ performance attributes.

**Key Finding:** The model identified **Raphinha** as the ideal replacement - a result that matched real-world transfer rumors reported by The Athletic and ESPN.

---

## 🎯 Business Problem

- **Context**: Liverpool loses 3 key African players (including Salah) to AFCON in January
- **Impact**: 6 crucial matches across 3 competitions during their absence
- **Challenge**: Salah had 23 goals + 10 assists - how do you replace that?
- **Solution**: Data-driven player scouting using similarity algorithms

---

## 🛠️ Technical Approach

### 1. **Data Cleaning & Feature Engineering**
- Started with 16,710 players and 65 variables
- Applied domain knowledge to filter realistic targets:
  - Age < 29 (Liverpool's transfer strategy)
  - Contract ending before 2026 (availability)
  - Value < £102M (Salah's market value)
  - Wages > £50K (quality threshold)
  - Excluded rival clubs (Man City, Chelsea, etc.)
- Final dataset: **1,606 players, 48 variables**

### 2. **Similarity Models**

#### **K-Nearest Neighbors (KNN)** ⭐ Primary Model
- Calculated euclidean distance across 32 player attributes
- Ranked top 10 most similar players
- **Results validated by ESPN**: 2 of top 3 recommendations matched their expert analysis

#### **K-Means Clustering** (Secondary)
- Unsupervised grouping into 8 clusters
- Cross-validated KNN results
- 40% overlap with KNN recommendations

### 3. **Key Attributes Analyzed**
```python
attributes = [
    'Finishing', 'Penalties', 'SprintSpeed', 'Dribbling',
    'ShortPassing', 'BallControl', 'Agility', 'Reactions',
    'Positioning', 'Vision', 'Composure', 'Stamina'
    # ... and 20 more
]
```

---

## 📊 Key Findings

### Top 5 Similar Players to Salah:

| Rank | Player | Club | Overall | Value | Key Strengths |
|------|--------|------|---------|-------|---------------|
| 1 | **Raphinha** | Leeds United | 82 | £46M | Speed (91), Stamina (84) |
| 2 | Oyarzabal | Real Sociedad | 85 | £77.5M | Versatility, Vision |
| 3 | Paulo Dybala | Juventus | 87 | £93M | Ball Control (93), Agility (92) |
| 4 | Y. Carrasco | Atlético Madrid | 84 | £45M | Pace (88), Dribbling (88) |
| 5 | L. Sané | Bayern Munich | 84 | £56M | Speed, Creativity |

### Model Validation
- **66.7% accuracy** compared to ESPN's expert-curated shortlist
- **Raphinha** identified as #1 target → Confirmed by The Athletic transfer news
- KNN outperformed K-Means for ranking similarity

---

## 📈 Visualizations

The notebook includes:
- **Polar charts** comparing player attributes
- **Distribution analysis** of player ratings
- **Correlation heatmaps** (discovered Reactions ↔ Overall = 0.88)
- **Interactive Plotly tables** for attribute comparison
- **Cluster visualization** using PCA dimensionality reduction

---

## 🚀 Getting Started

### Prerequisites
```bash
python 3.8+
pandas
numpy
scikit-learn
seaborn
matplotlib
plotly
```

### Installation
```bash
# Clone the repository
git clone https://github.com/yourusername/finding-similar-players.git
cd finding-similar-players

# Install dependencies
pip install -r requirements.txt

# Download the FIFA 22 dataset
# Visit: https://www.kaggle.com/datasets/stefanoleone992/fifa-22-complete-player-dataset
# Place FIFA22_official_data.csv.zip in the data/ folder
```

### Running the Analysis
```bash
jupyter notebook notebooks/player_similarity_analysis.ipynb
```

---

## 📁 Project Structure

```
finding-similar-players/
├── data/
│   ├── README.md              # Instructions to download FIFA dataset
│   └── FIFA22_official_data.csv.zip  (not included - see data/README.md)
├── notebooks/
│   └── player_similarity_analysis.ipynb  # Main analysis
├── images/
│   └── *.png                  # Visualizations for README
├── requirements.txt
├── .gitignore
└── README.md
```

---

## 🔍 Methodology Deep Dive

### Why KNN Over K-Means?
1. **Supervised vs Unsupervised**: KNN provides ranked similarity scores
2. **Interpretability**: Distance metrics directly show "how similar"
3. **Validation**: Can be compared against expert opinions (ESPN, The Athletic)

### Feature Engineering Insights
- **Correlation Discovery**: Reactions highly correlate with Overall (0.88)
- **Position Encoding**: Grouped 14 positions into Defender/Midfielder/Forward
- **Temporal Features**: Contract duration impacts transfer feasibility
- **Domain Filters**: Applied football industry knowledge (age, wages, rivals)

---

## 📊 Results & Impact

### Model Performance
- Successfully identified 2/3 of ESPN's expert recommendations
- Predicted Raphinha as top target → Confirmed by transfer news
- Excluded unrealistic options (goalkeepers, defenders, retired players)

### Business Value
- **Cost Efficiency**: Raphinha (£46M) vs alternatives (£56M-£93M)
- **Risk Reduction**: Data-driven vs gut-feeling recruitment
- **Scalability**: Model can be reused for any player across any position

---

## 🔮 Future Improvements

- [ ] Incorporate real-time match data (not just FIFA ratings)
- [ ] Add injury history and availability analysis
- [ ] Weight attributes based on Liverpool's tactical system
- [ ] Build interactive web app for live player comparisons
- [ ] Integrate transfer market dynamics (agent fees, wages)

---


## 🙏 Acknowledgments

- **Data Source**: [FIFA 22 Complete Player Dataset](https://www.kaggle.com/datasets/stefanoleone992/fifa-22-complete-player-dataset) (Kaggle)
- **Validation Sources**: ESPN, The Athletic
- **Inspiration**: Liverpool's actual transfer challenges during AFCON 2022


- GitHub: [@yourusername](https://github.com/yourusername)
- LinkedIn: [Your Name](https://linkedin.com/in/yourprofile)

---

**⚽ Finding the perfect player, one algorithm at a time.**
