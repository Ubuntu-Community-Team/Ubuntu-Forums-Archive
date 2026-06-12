---
title: "Benchmark"
date: 2008-05-18
forum: General Help
---

### Post by babylon2233 on 2008-05-18
I've try to find benchmarking tools that able to calculate FLOPS. I have try nbench but seems like it doesn't work perfectly on multi-core processor becuase when i see the cpu usage, only one core that been push to the limit(100 %) . I'm using Intel Q6600 which is quad-core . So, any of you have any suggestion.

Thanks

---

### Post by sdennie on 2008-05-18
I believe the theoretical max FLOPS for that CPU is 38.4 gigaflops.  However, in practice you aren't likely to get anywhere near that execpt on apps that have been very finely tuned.  To compute FLOPS, you just need an application with a known number of floating point operations and a timer however, computing FLOPS is application/compiler specific and so numbers will vary widely.  You may want to look at [http://lbs.sourceforge.net/](http://lbs.sourceforge.net/)

---

