---
title: "Top for SMP nodes"
date: 2007-02-07
forum: General Help
---

### Post by harisund on 2007-02-07
Here is the screenshot which describes what I want to see in Linux (yes, any Linux) .. 

[http://cct.lsu.edu/~hsunda3/screenshot.jpg](http://cct.lsu.edu/~hsunda3/screenshot.jpg)

Basically, my computer has 8 cores. And I do a decent amount of parallel programming, such as with OpenMP, and threads. 

I want to see all my CPUs in action. I can clearly see the graph on my Windows boot, but I want something that works on Linux as well. 

I was thinking top would be a good idea, but I am not able to get it show the CPU activity of all 8 cores. 

Any ideas fellows? And preferably something command line,though I guess I could X-Forward through SSH if required, *just to see my CPU activity in Linux.*

Thanks!

---

### Post by Zakalwe on 2007-02-12
apt-get install htop

---

### Post by ~LoKe on 2007-02-12
How about Conky?  It's not in the same league, but I imagine it would do the same thing?

---

