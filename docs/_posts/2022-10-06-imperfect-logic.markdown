---
layout: post
title:  "Imperfect Logic"
date:   2021-10-06 21:33:00 +0000
categories: math
usemathjax: true
---

Some textbooks on mathematical analysis will tell you that a function $f$ is continuous at $x$ if, for each $\epsilon>0$, there exists $\delta>0$ such that

$$|x-y|<\delta \implies |f(x)-f(y)|<\epsilon,$$

where $\|x\|$ represents the absolute value of the number $x\in\mathbb{R}$.

Since continuity can be inferred in many different ways, it is not often the case that one ends up using the definition above all that often. To remind ourselves of how to do it, let us pick a simple example, such as:

$$f(x)=x^2$$

for each $x\in\mathbb{R}$.

The proof that the quadratic function above is continuous, goes something like this.

<div class="proof">
Notice that 

$$|x^2-y^2|=|x-y||x+y|$$

for all $x,y\in\mathbb{R}$. If $\|x-y\|<\delta$, it follows that 

$$|x+y|\leq 2|x| +\delta.$$

If we select $\delta>0$ such that $\delta(2\|x\|+\delta)<\epsilon$, then 

$$|x^2-y^2|\leq \delta(2|x|+\delta)<\epsilon$$

which concludes the proof.
</div>

If you keep doing more exercises such as this, the definition of continuity becomes more and more natural, until you forget about any of the doubts that arose when you first looked at it, such as: where the hell does $y$ come from?

In the language of first-order logic, the definition of continuity given above translates to:

$$\forall \epsilon>0 \exists \delta>0 |x-y|<\delta \implies |f(x)-f(y)|<\epsilon$$

when it should read

\begin{equation}\label{eq:continuity}
\forall \epsilon>0 \exists \delta>0 \forall y\in\mathbb{R} |x-y|<\delta \implies |f(x)-f(y)|<\epsilon.
\end{equation}

Understanding the difference has everything to do with your own understanding of logic.

## The implication

The operator $ A\implies B$ between two logic sentences $A$ and $B$ has the following truth table:

| $A$ | $B$ | $A\implies B$ |
|-----|-----|---------------|
| $0$ | $0$ | $1$           |
| $0$ | $1$ | $1$           |
| $1$ | $0$ | $0$           |
| $1$ | $1$ | $1$           |

which is usually the source of many questions. In the particular case of continuity of a function $f$ at $x$, it means that for each $y$ satisfying $\|x-y\|\geq \delta$, the statement holds true, and although this might seem paradoxical, it reflects the fact that selecting $y$ outside the range prescribed by $\delta$ does not disqualify the function $f$ from being continuous at $x$, it just means that we made a poor choice of $y$.

## The negation

Following the rules of first-order logic, the negation ($\lnot$) of~\eqref{eq:continuity} yields:

$$\exists \epsilon>0 \forall \delta>0\exists y\in\mathbb{R} |x-y|<\delta \land |f(x)-f(y)|\geq\epsilon.$$

If a funtion $f$ satisfies the previous assertion for some $x$, then it is not continuous at $x$. Again, let us pick a simple example:

$$f(x) = \begin{cases}
1 \text{ if } x\geq 0\\
-1 \text{ otherwise}
\end{cases}.$$

<div class="proof">
For $x=0$, $\epsilon=1$ and for each $\delta>0$, we have that $y=-0.5\delta$ satisfies both $\|x-y\|=0.5\delta<\delta$ and $|f(x)-f(y)|=2\geq \epsilon$, hence $f$ is not continuous at $x=0$.
</div>

I close this article by pointing out an unspoken rule of first order logic: the negation of an assertion in logic does not change the domains of the variables. So, for example, the negation of $\forall x\in X P(x)$ is $\exists x\in X \lnot P(x)$.

## Summary
This post accomplishes 3 goals:
* It corrects the definition of continuity that is in the Appendix of the book "Introduction to Topological Manifolds";
* It provides some intuition into the definition of the implication operator;
* It explains how negation of logic assertions in first-order logic does not change the domains of the variables involved.