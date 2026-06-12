---
title: "Performance Problems"
date: 2007-09-24
forum: General Help
---

### Post by kjma on 2007-09-24
Hi again,

I installed Ubuntu with Wubi and i plan to install it as main OS soon. WINDOWS AWAY :)

But, untill I get myself some CDR's to burn it I still have to use the Wubi Ubuntu. 

Unfortunatly I do have some performance problems. I know how Linux runs on this Notebook (256MB Ram, 1.6GhZ) it should run very well. But it doesnt. Starting Aplications like xterm, firefox and so on takes a lot of time. If its started once it is ok. Is it because the Linux installation is in an NTFS filesystem? Or is there any other reason? (I had 7GB free disk space and gave 6 to ubuntu)


and: is a 'normal' ubuntu installation as easy as the wubi thing?

---

### Post by ago on 2007-09-25
Standard Ubuntu installation is very easy. The main advantages of wubi are that: 1. you do not have to burn a CD, 2. you do not have to repartition, 3. you can uninstall. But if you have made up your mind (that's what wubi is for) and you want to partition the HD,  by all means go with a real installation!

As for performance issues, no they are not normal at all. Every application in wubi should be extremely snappy. It would help us a lot if you could run some profiling software (using top, some disk monitor, disk performance utilities...) to find the bottlenecks. There is plenty of info on it (google ubuntu: benchmark hard disk...) and it's going to be an interesting exercise if you are new to linux. I would start to check disk I/O activity, disk fragmentation and cpu use.

---

### Post by kjma on 2007-09-25
Allright and where to send the infos to then? Here into the board?

---

### Post by kjma on 2007-09-25
```

Tasks: 106 total,   2 running, 103 sleeping,   0 stopped,   1 zombie
Cpu(s): 10.0%us,  1.3%sy,  0.0%ni, 85.3%id,  0.0%wa,  3.3%hi,  0.0%si,  0.0%st
Mem:    247836k total,   239364k used,     8472k free,     2548k buffers
Swap:   241200k total,    33920k used,   207280k free,    51296k cached

```

This looks normal so far? The word 'benchmark' give too much results in google, maybe you can name me a tool to benchmark disk i/o and so on.

---

