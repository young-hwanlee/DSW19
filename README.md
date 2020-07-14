# Learning to Infer Voltage Stability Margin Using Transfer Learning
Published in: 2019 IEEE Data Science Workshop (DSW). For more information, please refer to the paper.

## Abstract
Preventing voltage collapse is critical for reliable operation of power systems. A challenging problem is that the voltage stability margin, i.e., the distance from a given power proﬁle to the voltage stability boundary, is very computationally intensive to obtain. A novel machine learning based approach for real-time inference of voltage stability margin is developed, only needing a very small number of ofﬂine-computed voltage stability margin data. An accurate margin predictor is trained by ﬁrst training a binary stability classiﬁer and then transferring this pre-trained model to ﬁne-tune on the small data set of margins. Numerical simulations demonstrate that the proposed method signiﬁcantly outperforms Jacobian-based voltage stability margin estimation with even faster real-time computation.

## Neural Network Architecture
![transfer_learning-1](https://user-images.githubusercontent.com/67979833/87365130-708d2380-c543-11ea-85fc-a57aff6357e2.png)
1. As shown above, a neural network (NN) based binary classifier is trained from a large binary stability-labeled data set
2. The trained hidden layer of the NN is taken as a feature extractor
3. An additional layer of NN is added to fine-tune based on only a small margin-labeled dataset, resulting in a margin predictor
4. During training, weights of the first hidden layer transferred from the binary classifier are not altered, but only the second hidden layer and the output layer are fine-tuned

## Dataset
Refer to [1].

## Results
<table align='center'>
<tr align='center'>
<td> Scatter plot from using the proposed method </td>
<td> Scatter plot from using the smallest singular value (SSV) of the Jacobian matrix </td>
</tr>
<tr>
<td><img width="576" alt="scatter_plot" src="https://user-images.githubusercontent.com/67979833/87362688-53555680-c53d-11ea-8718-9d265b8195cd.jpg">
<td><img width="576" alt="scatter_plot_Jacobian" src="https://user-images.githubusercontent.com/67979833/87362687-53555680-c53d-11ea-9825-58e18d83bf46.jpg">
</tr>
</table>

Method | Jacobian's SSV | Direct Learning | Transfer Learning
---- | ---- | ---- | ----
Testing MSE | 15,876 | 4,817 | 1,624


## References
[1] Y. Lee, Y. Zhao, S.-J. Kim, and J. Li, “Predicting voltage stability margin via learning stability region boundary,” in Proc. 2017 IEEE 7th International Workshop on Computational Advances in Multi-Sensor Adaptive Processing. IEEE, 2017, pp. 1–5.
