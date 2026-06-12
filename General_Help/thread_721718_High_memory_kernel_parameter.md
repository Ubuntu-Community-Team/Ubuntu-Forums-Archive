---
title: "High memory kernel parameter?"
date: 2008-03-11
forum: General Help
---

### Post by b4rt on 2008-03-11
I am running ubuntu 7.10 with latest updates.

Right now I have 3 GB of DDR2 memory installed. When I want to insert another 1GB memory, my X server runs very slow. Do I have to add kernel parameters or something?

Memory passed the memory test, its not a hardware problem.

Thanks in advance,

Bart

---

### Post by dcstar on 2008-03-12
> **b4rt said:**
> I am running ubuntu 7.10 with latest updates.

Right now I have 3 GB of DDR2 memory installed. When I want to insert another 1GB memory, my X server runs very slow. Do I have to add kernel parameters or something?

Memory passed the memory test, its not a hardware problem.

Thanks in advance,

Bart

DDR2 works best with matched pairs of memory - then it can be addressed at double width.

Are you running 32 or 64 bit?

Anyway "mem=3000M" at the end of your boot string should limit the system memory to 3GB.

---

