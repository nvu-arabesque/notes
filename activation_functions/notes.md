
# Dont know what to Call it

## General Attentions

* **Global / Soft Attention:**
    - Attending to the entire input state space
    - Deterministic 
    - [Xu2015](http://proceedings.mlr.press/v37/xuc15.pdf)


* **Local / Hard Attention:**
    - Attending to the part of input state space
    - Local Attention pick a small number of segments from the input state space
    - Hard Attention randomly pick one segment of the input state space (stochastic)
    - [Xu2015](http://proceedings.mlr.press/v37/xuc15.pdf), [Luong2015](https://arxiv.org/pdf/1508.04025.pdf)
    

* **Self-attention:**
    - also known as intra-attention, is an attention mechanism relating different positions of a single sequence in order to compute a representation of the same sequence.
    - Can adopt any score functions (theoretically)
    - aka., "intra-attention"
    - [Cheng2016](https://arxiv.org/pdf/1601.06733.pdf)

    
* **Score Functions**
    
    - [Content-base attention](https://arxiv.org/abs/1410.5401): $score(s\_t,h\_i)=cosine\[s\_t, h\_i\]$
    
    - [Location-Based](https://arxiv.org/pdf/1508.04025.pdf): $\alpha\_{t,i}=softmax\({W\_a}{s\_t})$
        - Note: This simplifies the softmax alignment to only depend on the target position.
    
    - [General](https://arxiv.org/pdf/1508.04025.pdf): $score(s\_t,h\_i)={s\_t\^⊤}{W\_ah\_i}$
        - where $W_a$ is a trainable weight matrix in the attention layer.
        
    - [Dot-Product](https://arxiv.org/pdf/1508.04025.pdf): $score(s\_t,h\_i)={s\_t\^⊤}{h\_i}$
    
    - [Scaled Dot-Product](http://papers.nips.cc/paper/7181-attention-is-all-you-need.pdf): $score(s\_t,h\_i) = {s\_t\^⊤}{h\_i} / \sqrt{n}$
        - where $n$ is the dimension of the source hidden state.

    - [Additive](https://arxiv.org/pdf/1409.0473.pdf)/[Concat](https://arxiv.org/pdf/1508.04025.pdf): $score(s\_t,h\_i)={v\_a\^⊤} \tanh(W\_a\[s\_t; h\_i\])$


<!--you know that this list is very long ?-->
<!--yeah ... better not to use list, after we put more content -->





## Attention on TS -- potentially transferable to graph
not transformers, but applying attention on TS with `RNN`, `LSTM`, `1DConv`, etc. could be used as `benchmark` or simply `learning material`.

* [Enhancing the Locality and Breaking the Memory Bottleneck](https://arxiv.org/pdf/1907.00235.pdf): 
    - the LogSparse Self Attention thing can be used within each TS.
    - dont think it's suitable for attention between TS.
* https://arxiv.org/pdf/1703.07015.pdf
* https://arxiv.org/pdf/1809.04206.pdf
* https://arxiv.org/pdf/1901.10430.pdf





## Transformer Extension Ideas

**[Transformers](https://arxiv.org/pdf/1706.03762.pdf)**
Duh ~ 

**[Transformers Case Study](https://arxiv.org/pdf/2001.08317.pdf)**
Direct implementation of transformers on a single TS.
Easily replica-able, good starting point.

**[HAN](https://www.cs.cmu.edu/~./hovy/papers/16HLT-hierarchical-attention-networks.pdf)**
Hierachical Attention Networks: `soft attention + GRU` on words to represent each sentence, then repeat the same process with the sentences for document-level classification.
Here, sentences can be TS of companies and words be rolling TS chunks for each company. Lots of room to manipulation, imo.


**[Switch Transformers](https://arxiv.org/pdf/2101.03961.pdf)**
Based on the `MoE` concept, could be useful when involving multiple TS with different characteristics.


**[Longformer](https://arxiv.org/pdf/2004.05150.pdf)**
Could adopt for dealing with `long` sequence, both on a TS-level and a company-level, although it is not really a sequence at the company level.


**[Time2Vec](https://arxiv.org/pdf/1907.05321.pdf)**
Trainable positional encoding, could adopt but not of high priority.






## Efforts for Improving Computational Efficiency / Speed
To be considered later

* [Performer](https://arxiv.org/pdf/2009.14794.pdf)
* [Linformer](https://arxiv.org/pdf/2006.04768.pdf)
* [Reformer](https://arxiv.org/pdf/2001.04451.pdf)
* [Long Range Arena](https://arxiv.org/pdf/2011.04006.pdf)