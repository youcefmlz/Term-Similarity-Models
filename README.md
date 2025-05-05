# 📚 Term Similarity Estimation using TF-IDF and Word2Vec

This project explores two different approaches to estimating **term similarity** using a large corpus (`WikiText-103`):

1. **Task 1** – Sparse representation using **TF-IDF**
2. **Task 2** – Dense representation using **Word2Vec**

---

## 🧠 Task 1: TF-IDF Based Similarity (Sparse Representation)

### ✅ Goal
Estimate the similarity between terms by computing cosine similarity between their TF-IDF vectors.

### ⚙️ Workflow
- Preprocess the corpus:
  - Lowercasing, tokenization, stopword removal, lemmatization.
- Split the cleaned tokens into chunks of 1000 words.
- Use `TfidfVectorizer` to build a term-document matrix.
- Define a function `get_cosine_similarity(term1, term2)` that:
  - Looks up each word’s vector from the matrix.
  - Computes and returns cosine similarity between the two terms.

### 📌 Use Case
Suitable for **exact or near-exact matches** and identifying term importance within specific document contexts.

---

## 🤖 Task 2: Word2Vec-Based Similarity (Dense Representation)

### ✅ Goal
Estimate the semantic similarity between terms using vector embeddings learned from context.

### ⚙️ Workflow
- Preprocess the text:
  - Punctuation removal, tokenization, stopword removal, lemmatization.
- Chunk tokens into sequences of 1000 for training.
- Train a **Word2Vec** model with `vector_size=100`, `window=10`, and `min_count=2`.
- Define a function `get_similarity(term1, term2)` that:
  - Splits multi-word terms into individual tokens.
  - Averages their word vectors.
  - Computes cosine similarity between the averaged vectors.

### 📌 Use Case
Ideal for capturing **semantic similarity**, related meanings, and word associations learned from context.

---

## 🔍 Key Differences

| Feature         | Task 1: TF-IDF              | Task 2: Word2Vec           |
|----------------|-----------------------------|----------------------------|
| Model Type     | Sparse matrix                | Dense neural embeddings    |
| Representation | Frequency-based              | Contextual/semantic        |
| Similarity     | Lexical (exact match)        | Semantic (meaning-based)   |
| Output         | Cosine similarity            | Cosine similarity          |

---