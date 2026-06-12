---
title: "Compiling Blender from scratch"
date: 2014-07-22
forum: General Help
---

### Post by Tristan_Williams on 2014-07-22
Xubuntu 14.04 LTS
Dell Vostro 220
Intel Core 2 Duo
4 GB RAM



How much of a performance increase would I get from compiling Blender from scratch, versus the precompiled binary?

---

### Post by J_Me on 2014-07-22
Not much, the only reason to compile would be if you wanted to add extra features. Anyway what sort of speedups are you looking for.

---

### Post by Tristan_Williams on 2014-07-25
I'm not completely sure. I've heard that compiling from source causes increases in application speed versus prebuilt binaries. I know a small application like gedit or even Firefox won't benefit much from it, because there's not much going on. But I was thinking maybe a huge program like blender, with something as resource-consuming as a rendering engine, would benefit greatly from compiling from source

---

### Post by J_Me on 2014-07-27
I believe the people who build the precomplied package use ubuntu as their main OS so things are optimised for us users.
Unfortunately rendering is one of those dark arts at least for me anyway, however there are ways to speed things up but it takes some investigating, apart from the render tab settings and whether your using the CPU or GPU to render, try to use layering rather than rendering everything out in one go also look out for any 'cheats' on specific effects.
Enjoy

---

### Post by tgalati4 on 2014-07-27
I read an article regarding Gentoo Linux and a 2% speedup was observed compiling your own kernel (as was customary in Gentoo)--removing hardware support that your machine does not have.  A slightly smaller kernel, and less interrupts for hardware that does not exist means that the kernel can be be more efficient for your hardware.  Compiling applications may not show any improvement--unless you turn up the optimization level during compile time.  This is normally done anyway on big packages that require a lot of CPU power, so I doubt you will find savings.

The only way to know for sure is to create your build environment, compile your package (Blender, in this case) and run some benchmarks for Blender files that you are familiar with.  It might take a few hours to compile.  You might not notice any difference.  But I am curious.  I think the bigger gains are from compiling the kernel for your hardware.  But again don't expect more than 2% improvement.

---

### Post by Tristan_Williams on 2014-08-04
Wouldn't Blender count as a "big" package? I know it definitely takes a lot of CPU/GPU power

---

### Post by tgalati4 on 2014-08-04
Not only is blender a big package, but a lot of its performance depends on your video card and driver under linux:

[http://www.phoronix.com/scan.php?page=article&item=amd_nvidia_10cl&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_nvidia_10cl&num=1)

Recompiling would have no effect on GPU performance if your video card can't handle the graphics calls.

---

