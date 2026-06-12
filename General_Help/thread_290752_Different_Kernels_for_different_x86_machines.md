---
title: "Different Kernels for different x86 machines"
date: 2006-11-01
forum: General Help
---

### Post by muxecoid on 2006-11-01
Hi. I see several types of Linux kernels on the repositories. What kernel do I need to use for the following machines:

Two Intel Xeon Dual Core processors with ancient GeForce video?

One Intel Core 2 Duo processor with modern Intel Integrated video?

One AMD Athlon XP 2500+ processor with GF6800?

Thanks. What is the difference between generic and 386 kernels?

---

### Post by dcstar on 2006-11-02
> **muxecoid said:**
> Hi. I see several types of Linux kernels on the repositories. What kernel do I need to use for the following machines:

Two Intel Xeon Dual Core processors with ancient GeForce video?

One Intel Core 2 Duo processor with modern Intel Integrated video?

One AMD Athlon XP 2500+ processor with GF6800?

Thanks. What is the difference between generic and 386 kernels?

To make it simple:

[LIST=1]
[*]Use a K7 kernel for AMD processors
[*]Use a 686 kernel for any Intel CPU above a 386 (remember them?)
[*]Use a SMP kernel for any dual core/multiple processors
[*]Always leave a "Fall back" kernel installed!!
[/LIST]

---

### Post by muxecoid on 2006-11-02
> Use a K7 kernel for AMD processors
It's obsoleted by "generic" in latest Edgy release, is it any better than i386?
> Use a 686 kernel for any Intel CPU above a 386 (remember them?)
Yeah, I previously lived in a very poor country and even in 1998 having a 286 based computer was like luxury.
> Use a SMP kernel for any dual core/multiple processors
All of the 686 are SMP. So what? And how do I get a LiveCD with SMP?
> Always leave a "Fall back" kernel installed!!
Isn't it enough to test the new kernel for several hours before removing everything older?

---

