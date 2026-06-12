---
title: "Recompling Kernel"
date: 2008-02-11
forum: General Help
---

### Post by G-Unot on 2008-02-11
Hi guys, 

is there a good tutorial on recompling, or building a new kernel. i am on 2.6.22.14-generic and ive read tutorials on compling generic kernels, but i would like to recompile mine without vmplice. any ideas?

---

### Post by apetresc on 2008-02-12
> **G-Unot said:**
> Hi guys, 

is there a good tutorial on recompling, or building a new kernel. i am on 2.6.22.14-generic and ive read tutorials on compling generic kernels, but i would like to recompile mine without vmplice. any ideas?

Follow the same procedure as with any other kernel, but either apply the .patch file or do a ```
make menuconfig
``` to remove vmsplice before you run make.

But the security update to address the vulnerability you're probably worried about will be out in the repository in a few days, I'm certain :)

---

