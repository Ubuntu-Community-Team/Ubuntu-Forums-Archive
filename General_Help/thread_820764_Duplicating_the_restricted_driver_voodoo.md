---
title: "Duplicating the restricted driver voodoo"
date: 2008-06-06
forum: General Help
---

### Post by conundrumx on 2008-06-06
Hello all.  I've recently decided to trim and customize the kernel for my laptop, which in itself is not a terribly complex process.  However, the real challenge lies in duplicating the voodoo Ubuntu uses to make proprietary and bleeding edge hardware work so well.

I loaded the .config for 2.6.24-18-generic from /boot and made my changes, made a kernel deb (make-kpkg), and installed.  Booting into single user mode worked fine, so it's safe to say my kernel changes did not create something worthless.

However, I've no sound, no nvidia-glx (I tried reinstalling nvidia-glx-new to no avail), and no wireless.  I'm fairly comfortable with most things *nix, but proprietary drivers are something I've taken for granted in Ubuntu.  I feel like there is (or should be) some tool in existence that just takes a kernel .config and applies the driver voodoo, but perhaps that's optimistic.  Can anyone provide some insight on this?  Is the config file in /boot the exact one used to generate the generic kernel?

Hardware: Lenovo T61p, Intel C2D T9300, 4gb of RAM (another reason to make a custom kernel!), Nvidia Quadro FX 570, Intel 4965 (ABGN) wireless.

---

### Post by conundrumx on 2008-06-06
What do you know, further searching on Ubuntu's site instead of just google yielded [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) .  This should do the trick!

---

