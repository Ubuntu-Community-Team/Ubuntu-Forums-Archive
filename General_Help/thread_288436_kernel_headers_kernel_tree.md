---
title: "kernel headers kernel tree"
date: 2006-10-29
forum: General Help
---

### Post by zapcojake on 2006-10-29
Hello, I have some questions about some terms:
Kernel tree, what is it and whats it for?
Kernel headers what are they and what are they for?
I have compiled several kernels without using either of these and am just wanting some good info about them.

---

### Post by lloyd_b on 2006-10-29
1.  The kernel "tree" (at least in Debian - not really certain about Ubuntu) contains the kernel sources, plus the patches that have been applied by the distro.  

2.  The kernel headers are only needed by those who wish to build device drivers against the kernel, without installing the full kernel sources.  If you've got a full set of the kernel sources, then these are completely unnecessary.

Lloyd B.

---

### Post by zapcojake on 2006-10-30
So programs like Vmware need the headers to build themselves drivers.

---

