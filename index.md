# Papayas

Lets say that we want to say whether a papaya is tasty or not by looking at it. We can frame it as a machine learning problem by asking these questions:
1. (Domain set, X) What can we observe? Softness and color
2. (Target, Y) What do we want to predict? Tastiness
3. (Hypothesis, h) What kind of function models the relation between X and Y? h: X -> Y

We can also define the bad-ness of a hypothesis as the probability of it getting the tastiness of a random papaya wrong. 
That is, for some papaya (x, y) the bad-ness of a hypothesis h is 

![L(h) = P( h(x) \neq y )](https://render.githubusercontent.com/render/math?math=L(h)%20%3D%20P(%20h(x)%20%5Cneq%20y%20))


Here, L is called the true risk/loss/error. 

## Risk minimization
Now, we can pick an h which is least bad according to L. This algorithm is called *Risk minimization*.

For example, if we have 3 hypotheses


| Hypothesis | L(h_i) |
|------------|--------|
| h_1        | 0.2    |
| h_2        | 0.1    |
| h_3        | 0.3    |


Then, out of h1, h2, h3, the hypothesis h2 is the least bad.

h2 is not correct. But h2 is *approximately* correct.

The problem with this way of finding the bad-ness of h is that P( h(x) != y ) is evaluated over all the papayas in the universe - which is hard.

## Empirical Risk Minimization

A more practical way is to have finite papayas. We can collect Softness, Color and Tastiness data for some papayas. 
This will be our data sample, S

![S = \{ (X_1, Y_1), \cdots, (X_m, Y_m) \}](https://render.githubusercontent.com/render/math?math=S%20%3D%20%5C%7B%20(X_1%2C%20Y_1)%2C%20%5Ccdots%2C%20(X_m%2C%20Y_m)%20%5C%7D)

Now, we can define the bad-ness of a hypothesis h with respect to the sample S as the percent of papayas in S that h gets wrong.
That is,

![L_S(h) = \frac{|\{ i: h(x_i) \neq y_i \}|}{ m}](https://render.githubusercontent.com/render/math?math=L_S(h)%20%3D%20%5Cfrac%7B%7C%5C%7B%20i%3A%20h(x_i)%20%5Cneq%20y_i%20%5C%7D%7C%7D%7B%20m%7D)

Here, LS is called the empirical risk.


New Learning Algorithm: Pick the h that is least bad according to LS. This algorithm is called Empirical Risk Minimization (ERM).

Since ERM uses a finite data sample S, it will not always find a good hypothesis. We may sometimes get a bad hypothesis. 
So, ERM will *probably* give an *approximately* correct hypothesis.


Questions:
1. How close is LS to L?
2. How many hypotheses are we considering? (Finite or Infinite)
3. Is there a perfect h? (ie L(h) = 0)


