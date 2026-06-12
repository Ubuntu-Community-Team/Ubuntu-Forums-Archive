---
title: "question re: memory"
date: 2007-12-24
forum: General Help
---

### Post by scottym on 2007-12-24
When I run the htop or top command I get a different result from running the free command. For instance:
htop displays 406/621
free displays 599k/636k

So which is correct and why are they different?

---

### Post by nick_h on 2007-12-24
Both are correct.

The total memory figures differ because one is in K and the other in M.
621 * 1024 = 635,904

With the other figures I expect you are not comparing like for like.  The figure from htop will not include the cached data which is available to be re-used.  Look at the figures on the secong line of the output from free when you compare the two.

---

### Post by p_quarles on 2007-12-24
htop is displaying your RAM in Mebibytes (1 MiB = 1024 bytes), whereas free is displaying RAM in bytes. That explains the difference in in total memory available.

The difference in memory used is also pretty straightforward: run free, then subtract the number of bytes listed under "buffers" and "cached" from the amount listed in "used." You will see that this number comes out nearly the same as the total listed in htop, with any discrepancy explained by the fact that you did not run the two commands simultaneously.

---

