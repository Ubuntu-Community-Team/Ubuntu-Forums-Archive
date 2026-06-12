---
title: "kernel source"
date: 2006-07-21
forum: General Help
---

### Post by rbprogrammer on 2006-07-21
i'm trying to install vmware and it is asking me:
[INDENT]None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]   [/INDENT]
is there a package i can download from adept that would give me the kernel headers? because i am pretty sure vmware will not work unless i have those C Headers...

the path: [/usr/src/linux/include] does not exist yet on my computer

---

### Post by codejunkie on 2006-07-21
> **rbprogrammer said:**
> i'm trying to install vmware and it is asking me:
[INDENT]None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]   [/INDENT]
is there a package i can download from adept that would give me the kernel headers? because i am pretty sure vmware will not work unless i have those C Headers...
to install the kernel headers for your kernel run this command in a terminal
```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by rbprogrammer on 2006-07-21
wow, simple enough... i cant believe that was so easy, i figured it would have been harder.

thanks alot

---

