---
title: "Kernel and Pentium D (which processor fam.?)"
date: 2007-01-22
forum: General Help
---

### Post by rocketman768 on 2007-01-22
I downloaded the kernel source and am configuring the kernel. What is the best option for processor family? Some of the options are:

586/K5/5x86/6x86/6x86MX (currently selected)
Pentium-Classic
Pentium-MMX
Pentium-Pro
Pentium M
Pentium-4/Celeron(P4-based)/Pentium-4 M/Xeon
K6/K6-II/K6-III

Thanks!

---

### Post by jem7v on 2007-01-22
Isn't a Pentium D just a dual-core Pentium-4? It seems that family would be the most appropriate choice. [http://en.wikipedia.org/wiki/Pentium_D](http://en.wikipedia.org/wiki/Pentium_D)

---

### Post by rocketman768 on 2007-01-23
Ok. So, I can choose the Pentium 4 option. Is this the best one? Would the MMX provide more speed?

---

### Post by jem7v on 2007-01-23
It's probably the best one because it's more or less a Pentium 4, so I'd use the Pentium 4 kernel! To the best of my knowledge there have been significant changes to the Pentium architecture from the MMX days to the modern Pentium 4 cores. Using a kernel written for a chipset that hasn't seen the light of day in 8 years will most likely Not go faster.

---

### Post by jpolanco on 2007-01-24
What about a Celeron M? What processor family is it?

---

