---
title: "nvidia-9629 despite linux-restricted-modules?"
date: 2006-12-03
forum: General Help
---

### Post by Binärmensch on 2006-12-03
Hi there!

According to all installation manuals i've read you should have 2 choices in order to install the nvidia-drivers manually:
[LIST][*]Remove the linux-restricted-modules Package, or
[*]prevent the nvidia-kernel-module which comes along with it from loading by adding "nv" to the DISABLED_MODULES.[/LIST]

The point is: Only the first choice works for me. Adding "nv" to the DISABLED_MODULES doesn't do anything.

Using the first choice i've got the driver working, but it would be interesting to know why the DISABLED_MODULES don't seem to have any effect on my system. This could prevent me from problems may coming up in the future.

Some additional info regarding my system:
Ubuntu 6.10 64bit
nVidia 9629


Thanks in advance & greets from Austria, :)
- Binärmensch

---

