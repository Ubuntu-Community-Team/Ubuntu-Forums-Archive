---
title: "Making changes in kernel and testing dynamically"
date: 2014-04-19
forum: General Help
---

### Post by akshay-sulakhe on 2014-04-19
Hello friends,
                   I have currently installed Ubuntu 13.10 and i must make some changes in the kernel code. But as I need to test them again and again, do I need to recompile the entire kernel again. I will be making changes in SELinux only. While menuconfig, I tried to install SELinux as a module, but it is not possible. Am I doing something wrong. Kindly let me know. Any help or pointers are appreciated. Thank you for your time. Cheers. :-)

---

### Post by HermanAB on 2014-04-19
As far as I know, SELinux cannot be a dynamically loadable module.

The best way to experiment with kernels is in a Virtual Machine, otherwise you can too easily render your computer unbootable.

---

### Post by akshay-sulakhe on 2014-04-19
Yes, I am already testing it in a virtualized environment, but as you can expect, the time necessary to recompile is a lot. Anyway to cut it short?

---

### Post by HermanAB on 2014-04-19
Make should only recompile the things that changed.  SO the first compile is slow, thereafter should be faster.

---

### Post by akshay-sulakhe on 2014-04-19
Yes..I also believed so. I used the command make -j4 deb-pkg from link mentioned below, but still it is recompiling drivers right now. Dont know why.

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by tgalati4 on 2014-04-19
Most likely the drivers use hooks from SELinux and therefore any changes to that module will require all of the hardware modules to be recompiled--even if the changes are minor.  Since hardware modules (drivers) are known vectors for security problems, anything that touches SELinux will in turn touch the the hardware modules.

Learn a new hobby such a knitting to while away the time during compilations.

---

