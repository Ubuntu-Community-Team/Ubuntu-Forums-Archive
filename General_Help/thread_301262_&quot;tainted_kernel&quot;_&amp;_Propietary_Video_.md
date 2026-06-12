---
title: "&quot;tainted kernel&quot; &amp; Propietary Video Drivers"
date: 2006-11-16
forum: General Help
---

### Post by Cirrocco on 2006-11-16
I was looking around the results of a search for "nvidia" (I have a 440) and came across a thread that had people talking about installing video card drivers will "taint your kernel".   can anyone explain the logic behind that?

I guess I don't completely understand how a video card driver works.  

1) if I install an nvidia driver will my kernel be lessened in some way?
   -is this taint permanent?
   -when you install one; does it integrate itself into the kernel?  
   -thus breaking your video when you upgrade the kernel?
   -does a kernel upgrade completely remove the old video driver?

2) can't there be a layer (X?) outside the kernel that handles video such that you're free to upgrade your kernel without reinstalling your driver?
   -is this what an open driver would accomplish?

3) does there exist a open source video driver for nvidia cards that actually renders 3d graphics?
   -is it in/supported by the Ubuntu repos?

/full of questions :confused:

---

### Post by Joe_CoT on 2006-11-16
[What does it mean for a module to be tainted](http://www.tux.org/lkml/#s1-18)

What they mean by tainting your kernel is that the nvidia driver is closed source, and can't be reviewed to any large extent.

The linux kernel and modules are continuously maintained and tested, bugs fixed, optimized, etc. Same with the modules that come with it. However, what they mean by tainting your kernel is that that nvidia driver is a binary, and they can't do any of those things -- fix bugs, look for vulnerabilities, etc -- so any issues you have with your kernel can't be supported, ie, if you're running a propriety binary driver, don't put in kernel bug reports.

For the most part, running nvidia binaries works fine. However, since there's no oversight, flaws can go unnoticed; just recently someone discovered an exploit in the nvidia driver, which had apparently existed for years.


The nv driver is an nvidia driver which is open-source, and the one used by default before you switch to the nvidia binary. Howver, it doesn't handle 3d effects.

---

### Post by Cirrocco on 2006-11-17
I wonder if the NV driver will ever support 3d...
I suppose that would be an amazing feat of reverse engineering on the nvidia binary driver.

---

