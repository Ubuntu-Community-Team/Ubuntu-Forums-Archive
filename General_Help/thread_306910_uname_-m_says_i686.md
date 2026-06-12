---
title: "uname -m says i686"
date: 2006-11-25
forum: General Help
---

### Post by WalmartSniperLX on 2006-11-25
But I have a AMD sempron 64 3100+.

Im running the k7 kernel

Does this mean I should be running the 686 kernel? ](*,)

---

### Post by Ramses de Norre on 2006-11-25
No, I got this too on my amd with k7. Guess it's normal.
And is it the dapper kernel you're talking about?

---

### Post by WalmartSniperLX on 2006-11-25
> **Ramses de Norre said:**
> No, I got this too on my amd with k7. Guess it's normal.
And is it the dapper kernel you're talking about?

yeah its dapper

---

### Post by fragos on 2006-11-25
My Sempron 2800+ works well with the default i386 kernel.  I would think the 32 bit K7 kernel would be fine since it is for a 32 bit AMD.  686 is also compatable with AMD.

---

### Post by xopher on 2006-11-25
Isnt there a K8 kernel for dapper too? I used to use that one with my dapper .. in the days. ;)

---

### Post by syadnom on 2006-11-25
i686 is a general instruction set that is compatible with all modern x86 chip.  the default kernel is the i386 kernel in dapper and updating to the i686 will give you a bit better performance but most importantly support for multi-cpu or multi-core cpus.

there are also some other specific kernels like a k7 kernel that are the i686+support for k7 specific instructions not in the i686 instruction set such as 3dnow.

on a default dapper you will get i386
on a default edgy you will get i686
synaptic can help you install a more specific kernel for your cpu.

---

