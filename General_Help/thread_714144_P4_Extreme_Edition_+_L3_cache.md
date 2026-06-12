---
title: "P4 Extreme Edition + L3 cache"
date: 2008-03-03
forum: General Help
---

### Post by zyco321 on 2008-03-03
i noticed, that some programs are not telling the truth. e.g. cpuid, dmidecode, lshw are just saying that my p4ee has 1x l1 and 1x l2 cache, but nothing about the 2mb l3 cache

than "cat /proc/cpuinfo" says:
cache size      : 2048 KB

that sounds a little better, but it´s just the l3 cache and no l2 cache ;)

and finally dmesg (which is the only one where both were recognized):
CPU: Trace cache: 12K uops, L1 D cache: 8K
CPU: L2 cache: 512K
CPU: L3 cache: 2048K

so the question is, which one can i trust and how can i found out, if the l3 cache is really supported?

---

### Post by zyco321 on 2008-03-06
:confused:

---

