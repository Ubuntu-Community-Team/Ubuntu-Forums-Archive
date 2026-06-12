---
title: "Compile kernel without debug symbols"
date: 2007-08-04
forum: General Help
---

### Post by DrSpirograph on 2007-08-04
Hi,
I'm trying to compile my own kernel for Feisty, I've been following the instructions from:
[https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/kernel-baking.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/kernel-baking.html)

To create the kernel configuration I copied /boot/config-2.6.20-16-generic to /usr/src/linux/.config
and then used make menuconfig to make my changes.

However, when I compiled the kernel, the deb package was 10 times bigger than the normal kernel package (224 megs!).
Investigating the contents of the package, I noticed all the kernel modules were much larger than in the ubuntu kernel.

I'm guessing that maybe a butt-load of debugging info was included in the files or something, I didn't mess with any debug settings when I did make menuconfig, so why is this happening, and how can I fix it so that my kernel package is of a sane size?

---

### Post by DrSpirograph on 2007-08-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/kernel-package/+bug/90283](https://bugs.launchpad.net/ubuntu/+source/kernel-package/+bug/90283) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Fixed it using the instructions from this bug on Launchpad
[https://bugs.launchpad.net/ubuntu/+source/kernel-package/+bug/90283](https://bugs.launchpad.net/ubuntu/+source/kernel-package/+bug/90283)

---

