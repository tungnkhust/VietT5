# Introduction

- ViT5 is a pretrained Transformer-based encoder-decoder model for Vietnamese language (like T5 for English).
- They benchmarked ViT5 on 2 downstream tasks: Abstractive Text Summarization and NER
- ViT5 achieves SOTA results on Vietnamese Text Summarization
- ViT5 trained on the Vietnamese monolingual subset of CC100 and following the architecture and training methodology like T5
- ViT5 finetuned on 2 summarization datasets (Wikilingua and Vietnews) and one NER dataset (PhoNER)

## Detail
### 1. Architecture
- ViT5 follow the encoder-decoder architecture like T5. 
- T5 has five different configs of model size: small, base, large, 3B, 11B, and ViT5 only has 2 size: base (310M parameters) and large (866M parameters).
- ViT5 models have two different input and output length: 256 and 1024 length s.
- For the self-supervised training learning objective: ViT5 use the span corruption objective with a corruption rate of 15%

### 2. Vocabulary
- Vocabulary of ViT5 trained with SentencePiece method. They did pre-process on a 5GB subset of their pretraining corpus with care like normalizing punctuation, capitalization, splitting numbers.
- Size of vocabulary is fixed to 36K sub-words

### 3. Dataset
#### 3.1 Pretraining Data
- Dataset: CC100 Dataset (Monolingual Datasets) (January December 2018 Commoncrawl snapshots)
- Size for the Vietnamese Corpus: 138GB raw Text
- Process and filter -> 69GB shot paragraphs for 256-length and 71GB long paragraphs r 1024-length (length ?? -> short)

#### 3.2 Multitask training
##### 3.2.1 Vikilingua - Text Summarization
- Is a large scale multilingual corpus for abstractive summarization tasks. (including Vietnamese)

##### 3.2.1 Vietnems - Text Summarization
- Is a single document abstractive summarization datasets include news data from reputable Vietnamese news website (tuoitre.vn, vnexpress.net, nguoidautin.vn)
- The data consists of 150704 word level news articles with summary abstract and body text pars
- ViT5 had follow the filters pipeline by paper of Bartpho to deduplicate in train dev and test datasets.

##### 3.2.1 PhoNER_Covid19 Dataset - NER
- Is a dataset for recognizing named entities related to the COVID 19 domain in Vietnamese

### 4. Training Objective

### 5. Training Strategy

### 6. Evaluation
1. Text Summarization
- Metric: ROUGE (Recall - Oriented Understudy for Gisting Evaluation): ROUGE-1, GOUGE-2, GOUGE-L

2. NER
- Metric: Micro - F1
- 
### 7. Results
- Archive the highest score on 2 dataset (Wikilingue and Vietnews) (compare with PhoBert2PhoBert, mBart, mT5, BartPho)
- ViT5-base-1024 has the same score with sota (PhoBert - Large)