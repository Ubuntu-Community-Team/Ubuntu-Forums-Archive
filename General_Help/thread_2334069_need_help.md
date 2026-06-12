---
title: "need help"
date: 2016-08-16
forum: General Help
---

### Post by diesruine on 2016-08-16
hai everyone
which the better ubuntu for my new laptop with AMD A4-5000 Quad Core (1.5GHz) processor,4GB RAM?32bit or 64bit?

thanks before

---

### Post by jamesisin on 2016-08-16
Looks like that is a 64 bit capable processor.  Prefer the 64 bit version.

---

### Post by howefield on 2016-08-16
> **diesruine said:**
> which the better ubuntu for my new laptop with AMD A4-5000 Quad Core (1.5GHz) processor,4GB RAM?32bit or 64bit?

On the information that you provide I'd suggest the 64 bit version. 

Does that processor with integrated RADEON graphics ?

---

### Post by mastablasta on 2016-08-16
that's integrated Radeon which probably has fgrlx support on 14.04, and only Radeon (opensoruce driver) on 16.04.

it seems it has Radeon HD 8330 GPU is this supported by new amdgpu driver? 

In any case 14.04 64 bit would probably be the best way to go. at least for now.

More info in easy to read format:
[http://www.notebookcheck.net/AMD-A-Series-A4-5000-Notebook-Processor.92867.0.html](http://www.notebookcheck.net/AMD-A-Series-A4-5000-Notebook-Processor.92867.0.html)


TLDR:


> Performance


Due to the low clock speed of 1.5 GHz, the performance in poorly parallelized applications is quite modest and just slightly above the old E2-1800. However, if all 4 cores are busy, the performance equals the Sandy-Bridge-based Core i3-2377M. For office and multimedia tasks, the A4-5000 has sufficient power; however, it will reach its limits in more demanding applications and games.


Graphics


The SoC integrates a Radeon HD 8330 GPU with 128 shaders, which is based on the GCN architecture and clocked at 500 MHz (no Turbo). On average, the HD 8330 matches a Radeon HD 7470M or Intel HD Graphics 4000. Many recent games (as of 2013) are therefore hardly playable. However, some older or less demanding games will run fluently



---

### Post by diesruine on 2016-08-16
> On the information that you provide I'd suggest the 64 bit version. 

Does that processor with integrated RADEON graphics ?
with AMD Radeon HD 8330

---

### Post by howefield on 2016-08-16
> **diesruine said:**
> with AMD Radeon HD 8330

Then pay heed to the advice from mastablasta with regards no proprietary driver support in 16.04, which might not be a problem depending on what you use your computer for.

---

