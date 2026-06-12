---
title: "how to accurately determine a program's runtime?"
date: 2013-05-19
forum: General Help
---

### Post by jejones3141 on 2013-05-19
In the past few weeks I've been having a great time (and becoming more fluent in Haskell) by writing (most of; I borrowed the part that reads the input from another Haskell solution) and trying to optimize the heck out of a Haskell program to solve one of this year's Code Jam qualifying round programs. (I want to beat one of the C++ programs that succeeded with all inputs.)

If I turn on profiling, I can take a look at profiling output to determine runtime, but if I don't have it on, I figure time will do the trick... but I can run time N times and get different results N times. The latest version of my program gave time outputs ranging from

real    0m0.509s
user    0m0.488s
sys     0m0.016s

to

real    0m0.581s
user    0m0.564s
sys     0m0.008s

How much variation can I expect from time, and is there some way to either reduce it or another way to find out accurately how long it takes to run a program? (Goodness knows there are other processes using resources while my tests are running; they probably have an effect.)

---

### Post by tgalati4 on 2013-05-19
You can run a large population of tests (~30) and take an average.  Plot the histogram of the user time to make sure the distribution is gaussian (bell curve shaped).  Then you can compute the average, standard deviation and make uncertainty statements about your measurment.  For example:  User time is 0.52 seconds + or - 0.08 sec with 95% confidence.

You can use *strace* to get some insight into your code. Understand that the more you instrument your code, the more it affects the run time.  [Heisenberg]("http://en.wikipedia.org/wiki/Heisenburg_Uncertainty_Principle") had something to say about that.

You could also* nice* the process to apply a higher priority.  That should reduce the system time by running it more consistently at a higher priority.

There's an extensive Haskell library in linux, but I'm not sure how optimized it is compared with C++.  Anyone else know?

---

