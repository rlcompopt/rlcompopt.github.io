---
layout: index
---
[[Paper link]](https://openreview.net/pdf?id=DwEU2zXeHG) [[Slides link]](data/slides.pdf) [[Code link]](https://github.com/facebookresearch/RLCompOpt) [[ICML link]](https://icml.cc/virtual/2023/poster/23931)

We proposed a simple yet effective pipeline for pass ordering for program size reduction. 
- Key ideas
  - We don’t search good passes sequentially
  - Directly find a universal core set of pass sequences (termed coreset)
  - Make decision on top of this different action space to avoid the challenge of sparse reward
- The coreset
  - Optimize most programs
  - Require only an upfront search cost
- The policy
  - Learn to predict the _relative_ performance of coreset sequences
  - Apply the optimal coreset sequence to compile new programs at inference

In summary, we first identify a small set (termed coreset) of pass sequences that generally optimize the size of most programs. Then, a policy is learned to pick the optimal sequences by predicting the normalized values of the pass sequences in the coreset. 

The policy can be as simple as a multi-layer perceptron (MLP) that leverages the Autophase feature of a program. It can also be a graph neural network (GNN) that exploits the ProGraML graph of the program to predict the optimal pass sequence.

![Pipeline](images/pipeline.png)

