# Word2Vec 简介

Word2Vec 是一种用于自然语言处理的技术，通过将词语映射到向量空间中，使得计算机能够理解和处理文本数据。它由 Google 的 Tomas Mikolov 等人在 2013 年提出，主要有两种模型：CBOW（Continuous Bag of Words）和 Skip-gram。

## 工作原理

1. **CBOW 模型**：通过上下文词预测目标词。它使用上下文中的多个词来预测当前词。其目标是最大化以下条件概率：
    ```math
    P(w_t | w_{t-m}, \ldots, w_{t-1}, w_{t+1}, \ldots, w_{t+m})
    ```
2. **Skip-gram 模型**：通过目标词预测上下文词。它使用当前词来预测上下文中的多个词。其目标是最大化以下条件概率：
    ```math
    P(w_{t-m}, \ldots, w_{t-1}, w_{t+1}, \ldots, w_{t+m} | w_t)
    ```

## 优点

- **高效**：Word2Vec 使用神经网络进行训练，计算效率高。
- **语义关系**：生成的词向量能够捕捉词语之间的语义关系，例如“国王 - 男人 + 女人 ≈ 女王”。

## 应用

- **文本分类**：将文本表示为向量后，可以用于分类任务。
- **相似度计算**：计算词语之间的相似度，应用于推荐系统等领域。
- **机器翻译**：通过词向量表示，可以提高翻译的准确性。

Word2Vec 是自然语言处理中的重要工具，为文本数据的处理和分析提供了强大的支持。

## 代码实例

下面是一个使用 Gensim 库训练 Word2Vec 模型的简单示例：

```python
from gensim.models import Word2Vec
from nltk.tokenize import word_tokenize

# 示例文本数据
sentences = [
    "自然语言处理是人工智能的一个重要领域",
    "Word2Vec 是一种用于生成词向量的技术",
    "它能够捕捉词语之间的语义关系"
]

# 对文本数据进行分词
tokenized_sentences = [word_tokenize(sentence) for sentence in sentences]

# 训练 Word2Vec 模型
model = Word2Vec(sentences=tokenized_sentences, vector_size=100, window=5, min_count=1, workers=4)

# 获取词向量
word_vector = model.wv['自然语言处理']
print(word_vector)
```

在这个示例中，我们首先导入了所需的库，并定义了一些示例文本数据。然后，我们对文本数据进行了分词，并使用 Gensim 库训练了一个 Word2Vec 模型。最后，我们获取了“自然语言处理”一词的词向量并打印出来。