# CCSD-benchmark-for-code-summarization
This repo is the benchmark for source code summarization on C language.


# HGNN
RETRIEVAL-AUGMENTED GENERATION FOR CODE SUMMARIZATION VIA HYBRID GNN

A repository with the data for [the paper](https://openreview.net/pdf?id=zv-typ1gPxA). We share the dataset at [goole drive](https://drive.google.com/drive/folders/1NMRfcC1VgxjGGfVPrlRUrNSx2SGdtWeW?usp=sharing).


## Pre-Processing Stage
We crawlled 300+ projects such as Linux, redis, to construct our CCSD dataset. Totally, we collected 500k+ raw <function, summary> pairs, named with "all_functions.csv" at goole drive. The format is function_name (the name of extracted function), start_line (the start line number of this function in *.c file), end_line (the end line number of this function in *.c file), commemt (the comment of the function), start_comment, end_comment, and file_path.
Furthermore, Specifically, for summary, we extract the first sentence of the comment marked by "/**" and "*/". to keep the small functions, we set the threshold for tokenization to 150 and we will keep 130k+ functions. We named with "filter_functions.csv". 
We perform a de-duplication process and remove functions with cosine similarity over 80% to keep the dataset diverse as soon as possible. For the acceleration, we encode the raw functions into vectors with sklearn to compute the cosine similarity. After the de-duplication, we kept 95k+ <function, summary> pairs and named with "c_functions_all_data.jsonl.gz".

## Citation
If you find this dataset relevant to your work, please cite our paper:

```
@inproceedings{
liu2021retrievalaugmented,
title={Retrieval-Augmented Generation for Code Summarization via Hybrid {\{}GNN{\}}},
author={Shangqing Liu and Yu Chen and Xiaofei Xie and Jing Kai Siow and Yang Liu},
booktitle={International Conference on Learning Representations},
year={2021},
url={https://openreview.net/forum?id=zv-typ1gPxA}
}
```
