---
title: "Kernel Sources"
date: 2004-11-15
forum: General Help
---

### Post by Crisp on 2004-11-15
I'm running configure for a sound driver, and I come across this error:

```

checking for directory with kernel source... /usr/src/linux
checking for kernel version... The file /usr/src/linux/include/linux/version.h does not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

```

I tried specifying /usr/include/linux but obviously that's not right.  So, which package do I need to install?

I can find kernel-source-2.6.7 in the repo's, but I can't find 2.6.8 which is what I'm using.

-Crisp

---

### Post by Crisp on 2004-11-15
Would the package linux-source-2.6.8.1 be what I'm looking for?  I think so =)

-Crisp

---

### Post by az on 2004-11-15
Yes.

Instead of recompiling your whole kernel, just download your kenrel-headers (linux-headers-2.6)

Use that directory when prompted for your source tree...

---

