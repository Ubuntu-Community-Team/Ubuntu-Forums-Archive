---
title: "Cannot Install VMWare 5.5 on Ubuntu 6.06"
date: 2006-07-10
forum: General Help
---

### Post by acascianelli on 2006-07-10
Everything installs fine up to the point where it needs to compile the kernel modules.  When I point it to the kernel source files folder I get the following error...

What is the location of the directory of C header files that match your running kernel? [/usr/src/linux/include] /usr/src/

The path "/usr/src" is a kernel header file directory, but it does not contain the file "linux/version.h" as expected.  This can happen if the kernel has never been built, or if you have invoked the "make mrproper" command in your kernel directory.  In any case, you may want to rebuild your kernel.

What is the location of the directory of C header files that match your running kernel? [/usr/src/linux/include]

...reinstalling kernel sources doesnt change anything.  Version 5.0 and 5.5 worked fine on Ubuntu 5.10.  Does anybody know how to get it working on 6.06?

---

### Post by Jagot on 2006-07-10
Have you tried installing the headers:

```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by acascianelli on 2006-07-10
> **Jagot said:**
> Have you tried installing the headers:

```
sudo apt-get install linux-headers-`uname -r`
```

Thank you very much.  Works perfectly now.

---

