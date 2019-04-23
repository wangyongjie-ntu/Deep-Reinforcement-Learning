Prioritized Experience Replay is one strategy that tires to leverge this fact by changing the sampling distribution.

The main idea is that we prefer transition that does not fit well to our current estimate of the Q function, because these are the transition that we can learn most from.

We can define an error of a sample S = (s, a, r, s') as a distance between the Q(s,a) and its Target T(s):

error  = |Q(s,a) - T(s)|

For DDQN described above, T it would be <img src="http://latex.codecogs.com/gif.latex?\frac{\partial J}{\partial \theta_k^{(j)}}=\sum_{i:r(i,j)=1}{\big((\theta^{(j)})^Tx^{(i)}-y^{(i,j)}\big)x_k^{(i)}}+\lambda \theta_k^{(j)}" />

T(s) = r + \gamma \hat_Q(s', argmax_a Q(s', a))

One of the possible approaches to PER is proportional prioritization. The error is first conveyed to priority using this formula

![](http://latex.codecogs.com/gif.latex?\\ p = (error + \epsilon)^a)

Epsilon is a small positive constant that ensures that no transition has zero priority. Alpha, 0 <= \alpha <= 1 controls the different between high and low error. it dertimines how much prioritization is used. With alpha = 0, we would get the uniform case.

