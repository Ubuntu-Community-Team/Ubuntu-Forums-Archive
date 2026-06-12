---
title: "hibernate and multiple install"
date: 2007-10-12
forum: General Help
---

### Post by frigaut on 2007-10-12
Hi,

I have been asking this question to myself for some time and thought I would ask here...

Say I have 2 linux installs, on 2 different partitions (e.g. feisty on sda1 and gutsy on sda2), but only one home partition (say sda3).

Suppose now that I go and hibernate while running gutsy.

My question is: Can I boot in feisty, and do work accessing my home partition, and then resume gutsy? My take on that is that the hibernate leaves the home partition filesystem in a certain state, the feisty boot will modify that state, and then when I resume gutsy it will find a home partition/filesystem in a completely different state and likely mess it up?

Or is that somehow handled?

Thanks for your advice (just for completeness: I am not foolish enough to have tried that, but if I could I would surely have use for it).

---

### Post by kidders on 2007-10-13
Hi there,

Your suspicions are justified, imo. Using the same /home on more than one distro can be quite unstable, and compounding that with your hibernate scenario could be troublesome.

If you want to try it, I suggest being careful not to provoke any weird behaviour.

---

### Post by spupy on 2007-10-13
> **kidders said:**
> ...I suggest being careful not to provoke any weird behaviour.

= backup :O

---

