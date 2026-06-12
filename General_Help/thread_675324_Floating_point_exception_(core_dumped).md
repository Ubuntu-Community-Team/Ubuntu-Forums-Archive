---
title: "Floating point exception (core dumped)"
date: 2008-01-22
forum: General Help
---

### Post by Fraser484 on 2008-01-22
Hello all. I've been trying to run the Sofa Media Center and I keep getting a "Floating point exception (core dumped)". I've no idea what this means or how to go about fixing it. Any help would be greatly appreciated it.

I'm running Gutsy 7.10 btw.

---

### Post by ellgor on 2008-01-23
Hi,

While looking for something similar I actually looked at this particular program and as I didnt need it at the time I let it go, however, as I use kpackage, it comes under the heading of algorithims, mathematics (hence the floating point) there are quiet a few progs listed so have a look, hope this helps.

Regards, Ellgor.

---

### Post by heindsight on 2008-01-23
> **Fraser484 said:**
> Hello all. I've been trying to run the Sofa Media Center and I keep getting a "Floating point exception (core dumped)". I've no idea what this means or how to go about fixing it. Any help would be greatly appreciated it.

I'm running Gutsy 7.10 btw.
Floating point exception, means that the program tried to perform an illegal mathematical operation.
Usually something like trying to divide by 0 or taking the square root of a negative number.

If that happens, it means there's a bug in the program. 
I recommend that you try to collect as much information as possible about exactly what circumstances cause the floating point exception, and then submit a bug report.

---

