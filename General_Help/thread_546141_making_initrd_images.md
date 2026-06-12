---
title: "making initrd images"
date: 2007-09-08
forum: General Help
---

### Post by rihad on 2007-09-08
How can  I build and install custom kernel (through kernel-sources package) the same way it gets installed by Ubuntu? So that it has its own working initrd like /boot/initrd.img-2.6.20-15-custom?

---

### Post by rihad on 2007-09-09
bump

---

### Post by nick_h on 2007-09-10
Read the [Master Kernel Thread](http://ubuntuforums.org/showthread.php?t=311158).

You need the --initrd option when using the make-kpkg command.

---

### Post by sjatkins on 2008-02-03
A small example of how this is done would be extremely useful.   Any takers?

Especially since there is nothing called make-kpkg on my ubuntu system where I built the new kernel.  Is there some really good reason why an initrd is not made automatically as part of building the kernel BTW?

---

