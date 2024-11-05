## Probabilistic Relational Classifier


To make those predictions, we will use a Probabilistic Relational Classifier, the basic idea of which is that the class probability of Yi is a weighted average of the class probabilities of its neighbors. To initialize, we will use the ground-truth labels of our labeled nodes, and for the unlabeled nodes, we will initialize Y uniformly, for instance as P(Yunlabeled)=0.5–or if you have a prior that you trust, you can use that here. After initialization, you may begin to update all nodes, in random order, until convergence conditions or you have reached the maximum number of iterations. Mathematically, each repetition will look like this:

$$P(Y_v =c) = \frac{1}{\sum_{(v,u) \in E} A_{v,u}} \sum_{(v,u) \in E}A_{v,u} P(Y_u = c)  $$


We will update the nodes in random order until we reach convergence or our maximum number of iterations. We do not have to update in random order, but it has been shown empirically that it works very well across many cases, so we suggest random ordering. We must remember, however, that our results will be influenced by the order of nodes, especially for smaller graphs (larger graphs are less sensitive to that).

It should be noted, however, that there are 2 additional caveats:

1)Convergence is not guaranteed
2) Model cannot use node feature information




* node v, it's label $Y_v$
* class probability of node v is a weighted average of class probabilities of it's neighbours.
* For labeled nodes v,initilaize label $Y_v$ with ground truth $Y_v^*$
* For unlabeled nodes, initialize $P(Y_v = c) = 0.5$
*  **update** all nodes in a random order until convergence or until maximum number of iteraitons reached

* **Update** for each node v and label c(0 or 1)
$$P(Y_v =c) = \frac{1}{\sum_{(v,u) \in E} A_{v,u}} \sum_{(v,u) \in E}A_{v,u} P(Y_u = c)  $$

$P(Y_v =c)$ is the probability of node v having label c.

