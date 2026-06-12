---
title: "updated ubuntu now nothing working"
date: 2007-06-01
forum: General Help
---

### Post by djbenny on 2007-06-01
updated ubuntu through the updating program, now no sound and graphics gone bad??

there also appears to be getting more ubuntu selections on my list at boot up too there is now 7 different selections!

---

### Post by voxel on 2007-06-01
It sounds like you updated the kernel, because by defualt the GRUB boot menu will display the last 2 kernels (I'm pretty sure)

So if your boot menu looks something like this:
ubuntu-i386-generic 2.60.something
ubuntu-i386-generic 2.60.something recovery mode
ubuntu-i386-generic 2.60.something-else
ubuntu-i386-generic 2.60.something-else recovery mode
Windows XP

try booting the 3rd one down that *looks* like the entry on the top of the list, but has a **lower** kernel version (2.60.##). That should be your previous kernel, and hopefully everything should work. Let us know

---

### Post by djbenny on 2007-06-01
2 say 586 after them?

---

