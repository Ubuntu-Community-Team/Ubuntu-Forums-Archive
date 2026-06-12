---
title: "Serious Wxmaxima problem/flaw"
date: 2008-04-27
forum: General Help
---

### Post by Glaxed on 2008-04-27
Synopsis:
I have spotted what seems to be a pretty serious flaw in Maxima - where/how to fix it?

Background:
Maxima is a pretty dang advanced computer algebra system.
It is console-based, so I use wxMaxima to operate Maxima (a wx GUI interface).

Whenever I try to raise a given expression to a power which is not **_*explicitly*_** an integer, it goofs up.
Examples (// = comment);
```

(%i1) (3*x^2*n + 2*x^n + n); // intended (3x^2n + 2x^n + n)
(%o1) 2*x^n+3*n*x^2+n // got (2x^n + 3nx^2 + n)

(%i2) x^n * (x^2*n - x^n); // intended x^n(x^2n - x^n)
(%o2) x^n*(n*x^2-x^n) // got x^n(nx^2 - x^n)
// the correct answer would be (x^3n - x^2n) 

```This same flaw can be replicated with "objects" such as pi, e, or any other variable, variable expression, and some fractions (including some rational expressions :D).

Where can I report a bug - or is there something I am missing?
I don't want to report under the wxmaxima project, but that is technically what I am using...
help appreciated.

edit: wxmaxima version 0.7.1, maxima binary version 5.13.0

---

### Post by Glaxed on 2008-04-28
Hey guys, I think this is fixed in Maxima 5.15/wxMaxima .75.
Guess which OS I tried it on? - Yep - Windows.

I am BEGGING a math MOTU to put the new Maxima/wxMaxima in the repos - it is a very valuable upgrade.

---

### Post by Glaxed on 2008-04-30
```

(%i13) factor(6*x^2 + 17*X + 12);
(%o13) 17*X+6*x^2+12
(%i14) (3*X+4)*(2*X+3);
(%o14) (2*X+3)*(3*X+4)
(%i15) ratsimp(%);
(%o15) 6*X^2+17*X+12

```
**[COLOR="Red"]GAAAH! Now it won't factor trinomials![/COLOR]**
How can I contact Maxima developers??

---

### Post by kelvin911 on 2009-01-04
how can x^n*(n*x^2-x^n) = (x^3n - x^2n) ????????

retard

x^n * (n * x^2 - x^n) = n * x^(n+2) - x^(2n)

---

### Post by kelvin911 on 2009-01-04
> **Glaxed said:**
> ```

(%i13) factor(6*x^2 + 17*X + 12);
(%o13) 17*X+6*x^2+12
(%i14) (3*X+4)*(2*X+3);
(%o14) (2*X+3)*(3*X+4)
(%i15) ratsimp(%);
(%o15) 6*X^2+17*X+12

```
**[COLOR="Red"]GAAAH! Now it won't factor trinomials![/COLOR]**
How can I contact Maxima developers??

factor(6*x^2 + 17*X + 12);   <---------- x and X are different variable

try factor(6*x^2 + 17*x + 12);  retard

---

