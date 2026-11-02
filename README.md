# E-Commerce Customer Segmentation (RFM + K-Means + DBSCAN + PCA + t-SNE)

CA-2 Case Study: segment online-retail customers using **Recency, Frequency, Monetary (RFM)** features and derive actionable **marketing personas**.

## What the notebook does
1. Loads and cleans transactions (removes guest checkouts, cancellations, zero/negative quantity or price)
2. Builds RFM features, applies `log1p` and standardization
3. **K-Means**: elbow, silhouette, Davies-Bouldin to pick *k*
4. **DBSCAN**: k-distance plot + parameter grid, outliers labelled as noise
5. **PCA**: explained variance, loadings, 2-D projection
6. **t-SNE**: 2-D visualization of K-Means and DBSCAN segments
7. Compares algorithms and profiles each cluster
8. Maps clusters to **marketing personas** with recommended actions

## Files
| File | Purpose |
|------|---------|
| `customer_segmentation_rfm.ipynb` | Main notebook (already executed, outputs included) |
| `figures/` | All plots exported as PNG |
| `outputs/rfm_segments.csv` | RFM values + K-Means, DBSCAN labels and persona per customer |
| `outputs/persona_summary.csv` | Persona-level summary table |
| `requirements.txt` | Python dependencies |

## Dataset
Uses the [UCI Online Retail dataset](https://archive.ics.uci.edu/dataset/352/online+retail) if you place it at `data/Online Retail.xlsx` (or `data/online_retail.csv`).
If the file is missing, the notebook **automatically generates a synthetic transaction dataset with the same schema**, so it runs end to end without any download.

## Run
```bash
pip install -r requirements.txt
jupyter notebook customer_segmentation_rfm.ipynb
```

## Key results (synthetic data run)
- K-Means segments: Champions, At-Risk Loyalists, New / Promising, Hibernating / Lost
- Champions are ~18% of customers but ~67% of revenue
- DBSCAN isolates ~2.6% of customers as outliers (VIP / key-account candidates)
