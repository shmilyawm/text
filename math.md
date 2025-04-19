模型预测部分：  
\[  
y_i \approx \beta_0 + \sum_{j=1}^m \beta_j \times x_i^j  
\]  
当 \(\vec{x_i}\) 扩展为 \([1, x_i^1, x_i^2, \dots, x_i^m]\) 时：  
\[  
y_i \approx \sum_{j=0}^m \beta_j \times x_i^j = \vec{\beta} \cdot \vec{x_i}  
\]  
损失函数定义：  
\[  
\vec{\beta} = \arg \min_{\vec{\beta}} L(D, \vec{\beta}) = \arg \min_{\vec{\beta}} \sum_{i=1}^n (\vec{\beta} \cdot \vec{x_i} - y_i)^2  
\]  
将自变量和因变量放入矩阵 \(X\) 和 \(Y\) 后：  
\[  
\begin{align*}  
L(D, \vec{\beta}) &= \| X\vec{\beta} - Y \|^2 \\  
&= (X\vec{\beta} - Y)^{\top} (X\vec{\beta} - Y) \\  
&= Y^{\top}Y - Y^{\top}X\vec{\beta} - \vec{\beta}^{\top} X^{\top}Y + \vec{\beta}^{\top} X^{\top}X\vec{\beta}  
\end{align*}  
\]  
求梯度（使用 Denominator 布局约定）：  
\[  
\frac{\partial L(D, \vec{\beta})}{\partial \vec{\beta}} = \frac{\partial (Y^{\top}Y - Y^{\top}X\vec{\beta} - \vec{\beta}^{\top} X^{\top}Y + \vec{\beta}^{\top} X^{\top}X\vec{\beta})}{\partial \vec{\beta}} = -2X^{\top}Y + 2X^{\top}X\vec{\beta}  
\]  
将梯度设为零，求解最佳参数 \(\vec{\beta}\)：  
\[  
\begin{align*}  
-2X^{\top}Y + 2X^{\top}X\vec{\beta} &= 0 \\  
\Rightarrow X^{\top}X\vec{\beta} &= X^{\top}Y \\  
\Rightarrow \vec{\beta} &= (X^{\top}X)^{-1}X^{\top}Y  
\end{align*}  
\]  