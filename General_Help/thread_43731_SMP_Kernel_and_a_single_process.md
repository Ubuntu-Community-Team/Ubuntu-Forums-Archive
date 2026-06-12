---
title: "SMP Kernel and a single process"
date: 2005-06-23
forum: General Help
---

### Post by spacemonkey on 2005-06-23
I've just upgraded to the SMP kernel after learning that that is what I need to utilize hyper threading.  I like the dual CPU thing, and I definitely notice a difference when multitasking, but I've noticed a slow down in another area.  I participate in the seti@home program, and when running the SMP kernel, it appears that the setiathome process can't use more than 50% of my CPU, where with a non-smp kernel, I can use all 100%.  This causes a noticable slow down in the amount of time my CPU takes to handle one workunit.  Also, with the non-SMP kernel, I run setiathome with the lowest priority, so it doesn't cause any noticable slow down.  Is there anyway to use the SMP kernel but allow setiathome, or any other single process, use all of both processors, instead of just using all of one of the two processors.

---

