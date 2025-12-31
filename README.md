# VacSol-ML Datasets Repository

## Overview

Welcome to the official dataset repository for **VacSol-ML (ESKAPE)**, an open-source reverse vaccinology pipeline developed by the Atta-ur-Rahman School of Applied Biosciences (ASAB), National University of Sciences and Technology (NUST), Pakistan. VacSol-ML leverages advanced ensemble machine learning algorithms to analyze protein sequences and identify promising vaccine immunogens targeting ESKAPE pathogens (Enterococcus faecium, Staphylococcus aureus, Klebsiella pneumoniae, Acinetobacter baumannii, Pseudomonas aeruginosa, and Enterobacter spp.)—a group notorious for antimicrobial resistance.

This repository provides two curated, feature-engineered datasets derived from protein sequences, designed to support model training, evaluation, and prediction tasks in vaccine solubility (VacSol) and immunogenicity assessment. These datasets include thousands of computed descriptors (e.g., physicochemical properties, autocorrelation lags, and MHC binding scores) to facilitate reproducible ML research in vaccinology.

For the full framework, including sequence upload, analysis tools, and a standalone Python package, visit the [VacSol-ML Web Interface](https://mgbio.asab.nust.edu.pk/vaccines/eskapeml_upload/).

## Datasets

| Dataset | Rows | Columns | Description | Key Features |
|---------|------|---------|-------------|--------------|
| **VacSol-ML Dataset.csv** | 362 | 3,652 | Lag-based autocorrelation features for protein solubility prediction in ESKAPE contexts. Derived from physicochemical scales (e.g., CIDH920105 for hydrophobicity lags). Ideal for ensemble models focusing on sequence-derived lags. | - Protein_ID and Organism identifiers<br>- 30 lags per scale across 7+ scales (e.g., BHAR880101, CHAM820101)<br>- Geary/Moran autocorrelations (g1-g7 hierarchies)<br>- Gap-0 extensions for advanced descriptors |
| **VacSol-ML_DataSet_new_original.csv** | 412 | 895 | Comprehensive physicochemical and autocorrelation dataset for immunogenicity and solubility profiling. Includes global protein properties and window-based descriptors. | - Core attributes: aa_no (amino acids), molecular_weight, pH_charge, isoelectric point, Hydropathy_gravy, instability_index<br>- Immunogenicity scores: antigenicity_1, B-cell/MHC I/II probabilities and ranks<br>- Autocorrelations: GearyAuto/MoranAuto for hydrophobicity, flexibility, polarizability (1-30 lags)<br>- Dipeptide (D1001-D3100) and tripeptide descriptors for solvent accessibility, secondary structure, etc. |

Both datasets are in CSV format, with Protein_ID as the unique identifier (e.g., UniProt accessions like `tr\|Q9I0V8\|Q9I0V8_PSEAE`). They are preprocessed for direct use in Python (e.g., via pandas) or R, ensuring compatibility with scikit-learn, TensorFlow, or the VacSol-ML pipeline.

### Sample Data Preview
- **Dataset 1 Example Row** (truncated): `Protein_ID: tr|Q9I0V8|Q9I0V8_PSEAE, Organism: Pseudomonas aeruginosa, CIDH920105.lag1: 0.001988072, ...`
- **Dataset 2 Example Row** (truncated): `Protein_ID: tr|Q9I0V8|Q9I0V8_PSEAE, aa_no: 498, molecular_weight: 53867.82, pH_charge: -8.08, ...`

## Interactive Viewer
Browse and explore the datasets directly in your browser with our GitHub Pages-hosted viewer:
- [Live Demo](https://samavinasir96.github.io/vacsol-ml-datasets/)

Features:
- Tabbed interface for switching between datasets.
- Search, sort, and paginate (up to 50 rows or "All").
- Horizontal scrolling for wide tables.
- Direct CSV downloads.
- Responsive design for desktop/mobile.

Powered by DataTables.js and Bootstrap—fork and customize as needed!

## Usage Instructions
1. **Download**: Clone this repo or grab CSVs from the Releases tab.
2. **Load in Python**:
   ```python
   import pandas as pd
   df1 = pd.read_csv('VacSol-ML Dataset.csv')  # Shape: (362, 3652)
   df2 = pd.read_csv('VacSol-ML_DataSet_new_original.csv')  # Shape: (412, 895)
   print(df1.head())  # Explore
   ```
3. **Integrate with VacSol-ML**: Feed features into the ensemble models for immunogen ranking or solubility scoring. See the [standalone package](https://nustedupk0-my.sharepoint.com/:u:/g/personal/snasir_msib08asab_student_nust_edu_pk/EYZZwQRFfTtEtvw8q0nuoGMBF5evIWp6TF1taLLHMlTVLQ?e=FSl3sq) for batch processing.
4. **ML Workflow Example**: Use for feature selection (e.g., via Boruta) or training classifiers on solubility labels (if available).

These datasets were generated using standard bioinformatics tools (e.g., iFeature, Pfeature) on ESKAPE protein sequences from UniProt.

## Contributing & Citation
- **Issues/PRs**: Welcome! Report bugs or suggest enhancements via GitHub Issues.
- **Citation**: If using these datasets, please cite the VacSol-ML framework:
  > Nasir, Samavi & Anwer, Farha & Ishaq, Zaara & Saeed, Muhammad & Ali, Amjad. (2024). VacSol-ML(ESKAPE): Machine learning empowering vaccine antigen prediction for ESKAPE pathogens. Vaccine. 42. 126204. https://doi.org/10.1016/j.vaccine.2024.126204. 
  
  Also reference this repo: `https://github.com/yourusername/vacsol-ml-datasets`

---

*Last updated: December 31, 2025*  
*Contact: ASAB-NUST Vaccine Research Group (mgbio@asab.nust.edu.pk)*  

Star this repo if it helps your research! 🌟
