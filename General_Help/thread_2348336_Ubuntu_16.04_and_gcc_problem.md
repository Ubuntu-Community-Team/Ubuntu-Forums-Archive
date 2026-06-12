---
title: "Ubuntu 16.04 and gcc problem"
date: 2017-01-02
forum: General Help
---

### Post by Edward_Diener on 2017-01-02
I am running Ubuntu 16.04 and I can successfully use the default 64-bit  version of gcc to compile 64-bit code with the -m64 compiler switch. Yet  when I try to use the same default 64-bit version of gcc to compile  32-bit code using the -m32 compiler switch I receive during the  compilation the error:

/usr/include/c++/5/cstdio:41:28: fatal error: bits/c++config.h: No such file or directory
compilation terminated.

I  know I should be able to compile both 64-bit code and 32-bit code with  the 64-bit gcc compiler, but it looks like I am missing some header file  for 32-bit compilation. Does anyone know how I can determine which  package I need to install which includes the 'bits/c++config.h' header  file ?

---

### Post by steeldriver on 2017-01-02
IIRC you need to install the `gcc-multilib` package (and for C++, the `g++-multilib` package)

---

### Post by Edward_Diener on 2017-01-03
> **steeldriver said:**
> IIRC you need to install the `gcc-multilib` package (and for C++, the `g++-multilib` package)

That worked ! Thanks !

---

