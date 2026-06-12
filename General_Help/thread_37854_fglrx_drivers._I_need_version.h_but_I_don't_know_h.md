---
title: "fglrx drivers. I need version.h but I don't know how to recompile to get it."
date: 2005-05-28
forum: General Help
---

### Post by aap on 2005-05-28
I've downloaded the latest ATI fglrx drivers, converted them to .deb, and I've tried to install them. I'm stuck here:

```
aap@AndrewHP:/lib/modules/fglrx/build_mod $ sudo bash make.sh
ATI module generator V 2.0
=================
initializing. . .
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/version.h
``` 

I installed the source, and even symlinked it to `linux` in /usr/src.

I think I installed the kernel headers, but I'm not sure. I'm using 2.6.8.1.

I read that I have to recompile my kernel, and I don't know how to do that.

How can I do that or where can I get a version.h file?

---

### Post by melto on 2005-05-29
I think I'm having the same problem as you have and I'm searching also for help to fix that problem... The only difference is, that I'm using Ubuntu 5.04 Hoary edition..

---

### Post by melto on 2005-05-29
so I think I found it now in an earlyer entry. You only have to install the kernel headers and the problem should be fixed

[http://www.ubuntulinux.org/support/documentation/faq/compile-kernel-module](http://www.ubuntulinux.org/support/documentation/faq/compile-kernel-module)

that should do it..

melto

---

