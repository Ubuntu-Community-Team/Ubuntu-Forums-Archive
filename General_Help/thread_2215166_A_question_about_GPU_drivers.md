---
title: "A question about GPU drivers"
date: 2014-04-05
forum: General Help
---

### Post by Zirts on 2014-04-05
Hi!

So I was wondering, why is the installation of a GPU driver so risky on Linux? I mean, so many things can go wrong with just installing a video driver. And after that many things can go wrong if the system is updated while it has that driver installed.

But why is that? And what is the reason? Is it the way Linux is built or is it because the Nvidia and AMD driver devs are really lazy? And is there any hope that things will get better?

---

### Post by buzzingrobot on 2014-04-05
AMD and Nvidia do not release source code for their drivers or for the embedded software on their video cards.  They periodically release drivers for Linux as binary files. Individual distributions, like Ubuntu, must package these binary drivers for use in their repositories.

Without access to the source code for the drivers, Linux developers cannot know with certainty what a proprietary driver does. It's more than a bit like a black box.  For example, if the best way to fix a bug would be to modify the driver's source code, Linux developers cannot do it, and there is no assurance the Nvidia or AMD developers will.

Without access to the driver source, the only sure way to tell if/how a change to a piece of Linux software might be affected by a proprietary driver is to run it and see what happens. And, then, if the fault is with the driver, Linux devs cannot change it.

This is especially the case with the Linux kernel. Changes in the kernel can impact the drivers, and vice versa.  But, again, because they don't have access to the driver source, the kernel devs can only do so much.

Finally, add in the fact that, at any given, time, there is a very large and varied pool of distributions, kernels, and video drivers -- all of varying versions and age -- in use across the Linux community.

---

### Post by Mark Phelps on 2014-04-05
> So I was wondering, why is the installation of a GPU driver so risky on Linux? 

Installing video drivers is risky on ANY OS -- because if you force the wrong ones, you lose the display and that makes recovery very hard to do.

There's a common misconception carried over from MS Windows that one of the first things you do after installing a Linux distro is start hunting down drivers.  Not only is that a bad idea (as the installer has already done this for you) it's also almost entirely unnecessary.  

Proprietary video drivers bring extra functions, which unless you are doing hard core 3D gaming, are generally not needed.

IF you are seeing a desktop after you boot, you already have the video drivers installed.

---

