---
title: "algebra program?"
date: 2008-06-26
forum: General Help
---

### Post by aqaspecification on 2008-06-26
Hi, im currently trying to create a set of equations which allow for accurate headtracking using a nintendo wii remote which i hope to eventually implement in some 3d graphics programs and games, well ive currently hit a wall as i need to solve this equation for n:

solve(n=sqrt((((sqrt((((sqrt(((n*cos(e))^2)+(c^2)-(n^2))+(n*cos(e)))*cos(d))^2)+(b^2)-((sqrt(((n*cos(e))^2)+(c^2)-(n^2))+(n*cos(e)))^2))+((sqrt(((n*cos(e))^2)+(c^2)-(n^2))+(n*cos(e)))*cos(d)))*cos(g))^2)+(a^2)-((sqrt((((sqrt(((n*cos(e))^2)+(c^2)-(n^2))+(n*cos(e)))*cos(d))^2)+(b^2)-((sqrt(((n*cos(e))^2)+(c^2)-(n^2))+(n*cos(e)))^2))+((sqrt(((n*cos(e))^2)+(c^2)-(n^2))+(n*cos(e)))*cos(d)))^2))+((sqrt((((sqrt(((n*cos(e))^2)+(c^2)-(n^2))+(n*cos(e)))*cos(d))^2)+(b^2)-((sqrt(((n*cos(e))^2)+(c^2)-(n^2))+(n*cos(e)))^2))+((sqrt(((n*cos(e))^2)+(c^2)-(n^2))+(n*cos(e)))*cos(d)))*cos(g)))

as you can see its ridiculously long and im unable to solve it, does anyone know of a program that can solve it for n for me? i tried maxima but it wasn't up to it.

---

### Post by brian_p on 2008-06-26
> **aqaspecification said:**
> 

solve(n=sqrt((((sqrt((((sqrt(((n*cos(e))^2)+(c^2)-(n^2))+
(n*cos(e)))*cos(d))^2)+(b^2)-((sqrt(((n*cos(e))^2)+(c^2)-(n^2))+
(n*cos(e)))^2))+((sqrt(((n*cos(e))^2)+(c^2)-(n^2))+(n*cos(e)))*
cos(d)))*cos(g))^2)+(a^2)-((sqrt((((sqrt(((n*cos(e))^2)+(c^2)-(n^2))+
(n*cos(e)))*cos(d))^2)+(b^2)-((sqrt(((n*cos(e))^2)+(c^2)-(n^2))+
(n*cos(e)))^2))+((sqrt(((n*cos(e))^2)+(c^2)-(n^2))+(n*cos(e)))*
cos(d)))^2))+((sqrt((((sqrt(((n*cos(e))^2)+(c^2)-(n^2))+(n*cos(e)))*
cos(d))^2)+(b^2)-((sqrt(((n*cos(e))^2)+(c^2)-(n^2))+(n*cos(e)))^2))+
((sqrt(((n*cos(e))^2)+(c^2)-(n^2))+(n*cos(e)))*cos(d)))*cos(g)))

as you can see its ridiculously long and im unable to solve it, . . 

Isn't there a bracket missing from the equation?

---

### Post by traisen on 2008-06-26
Move n to the other side
Try asking in #math on the freenode irc server

---

### Post by Taxman415a on 2008-06-26
I agree you should carefully check your syntax, it doesn't seem right. (Though I really should brush up on one or more CAS, so I'm not sure.) But you should also note that not all expressions will have closed form solutions. In other words you can't always isolate n. It's just that the equations they gave you to solve in school you could.

Anyway there are several other algebra packages and a good way to find them is to run synaptic and search for algebra. Wade through there and you'll find things like axiom, kayali, mathomatic, yacas, and a few other more specialized ones that probably aren't what you want.

---

### Post by Topsiho on 2008-06-26
I do not know what kind of a solution you are looking for.
You give one equation, with at least 6 variables (n, b,c,d,g,a), and I probably missed some. No matter what mathematical program you use, generally speaking you will not get a solution such as n=1.5 or so.

You also do not mention what variable should be solved, which is correctly asked for by Maxima, so I tried some variables, such as n, or a, and some solutions need additional information.

I think you should think again :), it is not the algebra program you are using IMHO. Brackets seem to be OK, as Maxima does not complain....

Topsiho

---

### Post by aqaspecification on 2008-06-26
thanks for the help but no, i couldn't get a program to do it so eventually  i solved it myself with some help from an online program, the way to solve it was insanely complicated (all about noticing its self symmetry, the equation was a quadratic within a quadratic within a quadratic) and its no wonder the programs didn't manage it. i was solving it for n, the other variables are known but dynamic,
if any of you are interested the equation describes the following situation: in an irregular triangular based pyramid the edges of the base are known (a,b and c) and the angles corresponding to the face of each edge touching the tip of the pyramid are known (d,e and g), n denotes one of the unknown sides of the pyramid, clearly therefore there is only one non-negative solution of n).

---

### Post by Topsiho on 2008-06-27
OK, thanks for the information, so there is only one variable, which is on the left and on the right sides of the = sign.
The form in which the equation already is is Ok to solve it in steps (iteratively), by first GUESSING what n ought to be, and from that guess compute a new value for n, HOPING (it does not always behave like that, there are some conditions to be met, for that you should read a book on numerical analysis) that ***the new value is better than the guess***. Then you repeat this process, and in the end, if all is well (if n converges to a value), you end up with an answer, which MIGHT be the answer you are looking for.
The first guess is important, usually it should be in the near neighbourhood of the correct answer. AND if there are more solutions, MAYBE you find a solution you do not want.

If you are lucky this may not be as grim as you may fear, as in the case of finding the solution of

n = (n + a/n)/2

in which n is the square root of a.

Starting with n=1 (and a=5) one finds in a few steps (iterations) that n is (about) 2.2360..., which is correct (2.2360...^2=5).
Starting with n=3 one finds the same answer.

There is another solution that meets that n*n=a, and that is -2.2360...
If that is the solution that you want, you have to use another guess, -1, or -10, or so. Just try it to get a feel what this is all about :)
This case is very well behaved and can be found by using the Newton Raphson method for solutions like this, which is a very fast method.
If you want you can look for this NR-method too in a textbook on numerical analysis.

I hope you can use this technique, just try it.

Topsiho

---

### Post by Topsiho on 2008-06-27
I would like to add the following in case you are considering the Newton Raphson method. In this method you need the first derivative of f(n) if you want he solution of f(n)=0. If I remember it well the Newton Raphson method computes a better value for n from n=n-f(n)/f'n), in which f'(n) of course must not be nearly zero.
Now, to formulate f'(n) in your case is (and usually is) quite a job (you can of course let Maxima do that, that is true). In stead you can compute an approximation of f'(n) with

f'(n) = (f(n+h)-f(n-h))/(2*h)

Usually this approximation is quite good enough.

Topsiho

---

### Post by Topsiho on 2008-06-28
I returned to this posts to see whether there are reactions to it, but there are not yet any.
I use this opportunity to add to the computing of f'(n) that h should be small but not too small as division by a number too near zero is risky. From experimenting the best values generally speaking seem to be 0.01 or 0.001 or so (the formula is a centralized version of the definition formula for the (first) derivative function of f'(n). In this definition h approaches zero, as you probably know). Anyway, it is not necessary to compute f'(n) with utter precision, and to acquire convergence to a value for n, it is sometimes even necessary to multiply f'(n) with a positive factor smaller than 1, such as 0.5, 0.1, or so.

So ...

Topsiho

---

