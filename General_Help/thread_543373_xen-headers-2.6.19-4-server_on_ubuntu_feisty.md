---
title: "xen-headers-2.6.19-4-server on ubuntu feisty"
date: 2007-09-05
forum: General Help
---

### Post by echo0101 on 2007-09-05
I am trying to compile pci_hotplug support into a domu kernel.  I got the package xen-headers-2.6.19-4-server... when I try to compile it I get the following error:

root@mocha:/usr/src/xen-headers-2.6.19-4-server# make all
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
make[1]: *** No rule to make target `init/main.o', needed by `init/built-in.o'.  Stop.
make: *** [init] Error 2

the notes for the package mention that i need the corresponding linux-headers package, but I can't seem to find linux-headers-2.6.19-4-server.  I've even enabled backports repo.  am i doing something wrong?  how do i compile xen-headers?  thanks in advance.

---

### Post by Senthil Natarajan on 2007-09-25
I have the same problem.  Couldn't locate linux-headers-2.6.19-4-server.  Can anyone help?

---

