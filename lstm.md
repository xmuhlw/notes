**课题：面向训练过程的lstm权重偏度值异化分析研究**
需要研究 前向传播跟反向传播
[长短时记忆网络(LSTM)、沿时反向传播BPTT及梯度消失解决](https://zhuanlan.zhihu.com/p/80428276)
[LSTM训练过程推导 反向传播bptt](https://zhuanlan.zhihu.com/p/402373336)
[对于lstm的理解](https://zhuanlan.zhihu.com/p/354473016)
**[lstm的英文blog !]**(http://colah.github.io/posts/2015-08-Understanding-LSTMs/)
lstm ：可以设计一个记忆细胞，具备选择记忆的功能，可以选择记忆重要的信息，减少记忆负担,长短时记忆网络(Long Short Term Memory Network, LSTM)，是一种改进之后的循环神经网络，可以解决RNN无法处理长距离的依赖的问题
lstms ---They were introduced by Hochreiter & Schmidhuber (1997),

 **lstm是如何缓解梯度消失/爆炸**
**RNN中 的梯度消失/爆炸现象**是指后面时刻的梯度更新的时候，对于前面更远时刻的序列对参数更新是起不到作用的，梯度被近距离梯度主导，所以RNN无法捕捉与处理长距离依赖。

原始的RNN隐藏层里只有一个状态，就是h状态，对短期的输入非常敏感。在lstm中加入了C状态，用来保存长期的状态，称为单元状态（cell state）

遗忘门：forget gate：它决定了上一时刻的单元状态 c_t-1 有多少保留到当前时刻 c_t
输入门：input gate：它决定了当前时刻网络的输入 x_t 有多少保存到单元状态 c_t
输出门: output gate：控制单元状态 c_t 有多少输出到 LSTM 的当前输出值 h_t
gate 实际上就是一层全连接层，输入是一个向量，输出是一个 0到1 之间的实数向量。
当门输出为 0 时，任何向量与之相乘都会得到 0 向量，这就相当于什么都不通过（遗忘）
输出为 1 时，任何向量与之相乘都不会有任何改变，这就相当于什么都可以通过（记忆）
以上的参数是为了ht 而设置的，最终目的是ht  
 
 **权重**是w(权重)跟b(偏置)  ，通常是不同维度的矩阵，通过更新权重矩阵的值来更好的训练网络。 lstm中的激活函数是sigmoid函数跟tanh函数。

需根据误差E 计算权重矩阵W 和偏置向量b 的梯度，更新参数.
需更新的权重矩阵共8个: W(fh),W(fx);W(ih),W(ix);W(ch),W(cx);W(oh),W(ox).
需更新的偏置向量共四个：b(f),b(i),b(c),b(o)
另外输出层权重矩阵和偏置向量各有一个：V，b(v)

  
  
