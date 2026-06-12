---
title: "Hand Compiled Kernel and Nvidia"
date: 2004-12-12
forum: General Help
---

### Post by Technoviking on 2004-12-12
I'm planning on rolling my own 2.6.9 kernel for my brand new warty install.  I am just curious as to the best method for getting the nvidia drivers working are?  Should I compile my own kernel then remove all the nvidia stuff that ubuntu has installed, then get nvidia's shell script to install?  or is there a package that will do the same thing for me? (nvidia-kernel-source is in the repo is this what i should use?)

---

### Post by Technoviking on 2004-12-13
So I figured this out if anyone is interested in the solution:

1. Compile/Install new vanilla kernel
2. Remove default Ubuntu kernels (make sure your new kernel works fiirst)
3. Remove all of the other nvidia stuff, including restricted-modules
4. Download nvidia driver installer from nvidia.com
5. Run installer

This is by no means an actual guide or anything like that.

---

