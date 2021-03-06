# ID3、C4.5、CART三种算法优缺点比较

# ID3

ID3算法十分简单，核心是根据“**最大信息熵增益**”原则选择划分当前数据集的最好特征，信息熵是信息论里面的概念，是信息的度量方式，**不确定度越大或者说越混乱，熵就越大**。在建立决策树的过程中，根据特征属性划分数据，使得原本“混乱”的数据的熵(混乱度)减少，按照不同特征划分数据熵减少的程度会不一样。在ID3中选择熵减少程度最大的特征来划分数据（贪心），也就是“最大信息熵增益”原则。

同时这是最早提出的一种决策树方法，使用上述信息增益的方式建立。
**缺点：只能处理离散型属性，并且对倾向于选择取值较多的属性**

原因：信息增益反映的给定一个条件以后不确定性减少的程度,必然是分得越细的数据集确定性更高,也就是条件熵越小,信息增益越大。

# C4.5

C4.5算法流程与ID3相类似，只不过将信息增益改为信息增益比，以解决偏向取值较多的属性的问题，另外它可以处理**连续型属性**。

# CART

CART是一棵二叉树，采用**二元切分法**，每次把**数据切成两份**，分别进入左子树、右子树。而且每个非叶子节点都有两个孩子，所以CART的叶子节点比非叶子多1。相比ID3和C4.5，CART应用要多一些，**既可以用于分类也可以用于回归**。CART分类时，使用基尼指数（Gini）来选择最好的数据分割特征，**gini描述的是纯度，与信息熵的含义相似**。CART中每一次迭代都会降低GINI系数


相对于ID3使用的信息增益，CART中用于选择变量的不纯性度量是Gini指数，总体内包含的类别越杂乱，GINI指数就越大（跟熵的概念很相似）。

GINI指数： 
1、是一种不等性度量； 
2、通常用来度量收入不平衡，可以用来度量任何不均匀分布； 
3、是介于0~1之间的数，0-完全相等，1-完全不相等； 
4、总体内包含的类别越杂乱，GINI指数就越大（跟熵的概念很相似）

CART分析步骤：

1、从根节点t=1开始，从所有可能候选S集合中搜索使不纯性降低最大的划分S*，然后，使用划分S*将节点1（t=1）划分成两个节点t=2和t=3； 
2、在t=2和t=3上分别重复划分搜索过程。

基尼不纯度指标：

在CART算法中, 基尼不纯度表示一个随机选中的样本在子集中被分错的可能性。基尼不纯度为这个样本被选中的概率乘以它被分错的概率。当一个节点中所有样本都是一个类时，基尼不纯度为零

离散和连续目标变量的区别：

同时，如果目标变量是标称的，并且是具有两个以上的类别，则CART可能考虑将目标类别合并成两个超类别（双化）； 
如果目标变量是连续的，则CART算法找出一组基于树的回归方程来预测目标变量。