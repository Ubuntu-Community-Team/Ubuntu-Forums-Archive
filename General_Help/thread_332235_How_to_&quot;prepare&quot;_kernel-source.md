---
title: "How to &quot;prepare&quot; kernel-source?"
date: 2007-01-05
forum: General Help
---

### Post by xShrimp on 2007-01-05
Hiya,
I want to install Fuse 2.6.0, but when I use the command 
```
./configure --enable-kernel-module
```
I get at the bottom:
```
=== configuring in kernel (/usr/src/fuse-2.6.1/kernel)
configure: running /bin/bash ./configure --prefix=/usr/local  '--enable-kernel-module' --cache-file=/dev/null --srcdir=.
checking for a BSD-compatible install... /usr/bin/install -c
checking kernel source directory... Not found
configure: error:
        *** Please specify the location of the kernel source with
        *** the '--with-kernel=SRCDIR' option
configure: error: ./configure failed for kernel
```

So then I unpack kernel-source, and used the command:
```
./configure --with-kernel=/usr/src/kernel-source-2.4.27
```

I get:
```
=== configuring in kernel (/usr/src/fuse-2.6.1/kernel)
configure: running /bin/bash ./configure --prefix=/usr/local  '--with-kernel=/usr/src/kernel-source-2.4.27' --cache-file=/dev/null --srcdir=.
checking for a BSD-compatible install... /usr/bin/install -c
checking kernel source directory... /usr/src/kernel-source-2.4.27
checking kernel build directory... /usr/src/kernel-source-2.4.27
checking kernel source version... Not found
configure: error:
        *** Cannot determine the version of the linux kernel source. Please
        *** prepare the kernel before running this script
configure: error: ./configure failed for kernel
```

Can someone teach me to somehow "prepare" the kernel?

---

### Post by pay on 2007-01-05
Try ```
./configure --with-kernel=/usr/src/linux
```

---

### Post by xShrimp on 2007-01-05
/usr/src/linux doesn't exist
```
=== configuring in kernel (/usr/src/fuse-2.6.1/kernel)
configure: running /bin/bash ./configure --prefix=/usr/local  '--with-kernel=/usr/src/linux' --cache-file=/dev/null --srcdir=.
checking for a BSD-compatible install... /usr/bin/install -c
checking kernel source directory... /usr/src/linux
checking kernel build directory... /usr/src/linux
checking kernel source version... Not found
configure: error:
        *** Cannot determine the version of the linux kernel source. Please
        *** prepare the kernel before running this script

```

when I try "./configure" with kernel-source
```
bash: ./configure: No such file or directory
```
another way to compile??

---

### Post by xShrimp on 2007-01-07
anyone?

---

