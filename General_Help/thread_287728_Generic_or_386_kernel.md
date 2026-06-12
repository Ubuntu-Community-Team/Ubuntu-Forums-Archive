---
title: "Generic or 386 kernel ?"
date: 2006-10-29
forum: General Help
---

### Post by abelthorne on 2006-10-29
Hello,
My PC has an AMD Sempron CPU. When I used Dapper I used the k7 kernel, which supposedly was the one most suited for my CPU (from the information I had gathered on websites).
Now that I've upgraded to Edgy, it seems that the k7, 686 and such kernels are obsolete and a new one has appeared, which is named "generic".
Currently, I've switched back to 386 kernel as I don't really know what is the generic one.

Is the generic kernel supposed to replace everything that is not 386 CPU (with better performances) ? Or maybe it's even a first step to replace every CPU, including 386 ones (auto-detecting the CPU model or such) ?

With my CPU, should I use the generic kernel or stick with the 386 one ?

---

### Post by jocko on 2006-10-29
Afaik, the -generic kernel contain the optimisations that were in the old -k7 and -686 kernels. The -386 kernel is mostly to keep compatibility with really old processors.

---

### Post by Melcar on 2006-10-29
> **abelthorne said:**
> Hello,
My PC has an AMD Sempron CPU. When I used Dapper I used the k7 kernel, which supposedly was the one most suited for my CPU (from the information I had gathered on websites).
Now that I've upgraded to Edgy, it seems that the k7, 686 and such kernels are obsolete and a new one has appeared, which is named "generic".
Currently, I've switched back to 386 kernel as I don't really know what is the generic one.

Is the generic kernel supposed to replace everything that is not 386 CPU (with better performances) ? Or maybe it's even a first step to replace every CPU, including 386 ones (auto-detecting the CPU model or such) ?

With my CPU, should I use the generic kernel or stick with the 386 one ?


I'm using the generic one with my Sempron 3300+ with no problems yet.  I am having performance problems with my ATI chip (200M) but I don't know if it's kernel related (I used to get better performance under Dapper with the K7 kernel).

---

### Post by ~LoKe on 2006-10-29
The generic kernel can be used with all processors, 32bit, 64bit, etc.

---

### Post by cls1chuck on 2006-10-30
Does this mean the various CPU architecture-specific kernels (k7, 686, etc.) are no more, or is this an interim kernel until the next release?

---

