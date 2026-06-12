---
title: "i386/i486/i586/i686 - Questions"
date: 2004-11-15
forum: General Help
---

### Post by d0gbert on 2004-11-15
I'm running Ubuntu on a notebook w/ a PIII, so I recenlty upgraded the kernel to one that was optimized for the i686 architecture.

I'm assuming the Ubuntu CD-ROM was optimized for i386 because it's easier to produce a CD for a single architecture also maximizes the number of potential users for obvious reasons.

My question was, what kind of performance hit does compiling source code for the i386 architecture have if I'm actually running it on a i686?  I certainly haven't noticed a lack of performance but thought it was worth asking.

Thanks!
d0gbert

---

### Post by TravisNewman on 2004-11-15
Not much at all... when you compile from source you're essentially compiling it to your own system. I don't think many people make source code for each architecture, it's basically just what your compile options are. I don't KNOW these compile options (I know how to set them in Gentoo) but honestly you don't get a big enough performance boost in compiling than just installing packages from apt, to warrant compiling time. at least not in my opinion.

---

### Post by jdong on 2004-11-15
Oh boy, I don't want to start a flame war from Gentoo users here, but the truth is:

Optimization -- especially if not done carefully -- have so many detrimental effects that it outweighs any small performance increases it may bring.

Ubuntu currently is optimized for i486 (-march=i486) and geared at pentium 4's (-mcpu=pentium4). This means that Ubuntu will require an i486 to run, but will take advantage of additional P4 features if it has a P4 to run on.


The default kernel is not optimized at all (generic i386), but i686 (AMD, Pentium Pro+)and k7 (Athlon XP, seems also to work on Athlons) optimized kernels are provided.


I honestly see no difference in which kernel I use -- they both launch Openoffice, render firefox pages, and pump out UT2004 frames identically...


So, honestly it doesn't matter!

---

### Post by Klunk on 2004-11-16
Does the installer select the right kernel for your system? I am more than happy with performance on my machine, running on an AMD Duron 1Ghz. Just wondering if I am using anything other than the base 1386 kernel.

---

### Post by HiddenWolf on 2004-11-16
[QUOTE=Klunk]Does the installer select the right kernel for your system? I am more than happy with performance on my machine, running on an AMD Duron 1Ghz. Just wondering if I am using anything other than the base 1386 kernel.[/QUOTE]

It does not do so at the moment, and won't do so in the future.
The reason being that while the kernel is small, a hell of a lot of modules come with it.
Supplying multiple kernels on the cd would require more then a single cd.

The single cd is a great bonus and goal of ubuntu, and so they won't ship multiple kernels.

---

