---
title: "R Language Memory Limits"
date: 2007-03-06
forum: General Help
---

### Post by dkatz on 2007-03-06
I am an R user trying to get around the 2Gig memory limit in Windows, so here I am days later with a working Ubuntu, and R under Ubuntu. But - the memory problems seem worse than ever. R code that worked under windows fails, unable to allocate memory. 

Searching around the web, it appears that the problem may be the ability to find contguous memory for my big vectors, but a fresh boot of Ubuntu does not help either. 

Which way to go? 

1) Try to install 64-bit version for bigger address space. Would this help? Is this workable for my Athlon 64 Dual-core? (the live cd seems to work but I never got it to boot after a disk install, but then the 386 version was no better until I learned more about Grub...I could try again if this might solve the problem) 

2) Recompile R to get bigger memory capability? (I'll have to cross-post to some R forums too)
This will be a challenge for a Linux newbie...like me. 

3) Any other suggestions? My goal is to create a bigger neural network than fits in my Windows R version.

---

