---
title: "I cannot install Desktop Drapes, says I need to install Mono"
date: 2008-05-08
forum: General Help
---

### Post by Lord Xeb on 2008-05-08
I just reinstalled mono and I still cannot install desktop drapes.


```
root@nathan-laptop:/home/nathan/Desktop/drapes-0.5.2# ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... none
checking for intltool >= 0.21... 0.36.2 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for a BSD-compatible install... /usr/bin/install -c
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for UNMANAGED_DEPENDENCIES_MONO... no
checking for UNMANAGED_DEPENDENCIES_MINT... no
configure: error: You need to install mono
root@nathan-laptop:/home/nathan/Desktop/drapes-0.5.2# 
```

---

### Post by shirilover on 2008-05-08
Did you install the -devel and -dev packages as well?

---

### Post by Lord Xeb on 2008-05-13
:/ Not sure, I just gave up and started fidgiting with something else <_<

---

### Post by strabes on 2008-05-13
Why don't you just install the drapes package in the ubuntu repositories?

sudo aptitude install drapes

---

