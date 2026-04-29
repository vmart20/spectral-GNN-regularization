## Overview
Official code for the AISTATS 2026 paper: **"Generalization Bounds for Spectral GNNs via Fourier Domain Analysis"**.

## Before cloning the repository (Requires Git LFS)

This repository uses [Git LFS](https://git-lfs.com/) (Large File Storage) to handle the dataset files. You must have Git LFS installed before cloning.

```bash
# Install LFS (Ubuntu/Debian)
sudo apt-get install git-lfs
git lfs install
git clone https://github.com/vmart20/spectral-GNN-regularization.git
```

## Regularizer
For the regularization experiment, we compute a normalized adjacency matrix and use polynomial filters with eigenvalues mapped to [0,1]. To run the main node classification experiments on the benchmark datasets (Cora, Citeseer, Chameleon, Squirrel) with the energy-weighted regularizer:

```bash
python run_spectral_gnn.py --dataset cora --base chebyshev --use-reg 1
```

To run without regularizer:

```bash
python run_spectral_gnn.py --dataset cora --base chebyshev --use-reg 0
```

## Bound computation

To compute the non-linear FTGC bounds and stability bounds, we use the normalized adjacency matrix, without additional spectral rescaling of the eigenvalues:

```bash
cd theoretical_validation
python run_arxiv_validation.py --dataset ogbn-arxiv --base chebyshev --out_dir ./results
```

