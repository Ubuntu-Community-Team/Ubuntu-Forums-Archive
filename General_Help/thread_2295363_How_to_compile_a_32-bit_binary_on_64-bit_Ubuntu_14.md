---
title: "How to compile a 32-bit binary on 64-bit Ubuntu 14.04"
date: 2015-09-18
forum: General Help
---

### Post by Tony T on 2015-09-18
I would like to compile this sgminer program in 32 bits:
[https://github.com/sgminer-dev/sgminer/tree/develop](https://github.com/sgminer-dev/sgminer/tree/develop)

It compiles nicely in 64 bits using:

git submodule init
git submodule update
autoreconf -i
CFLAGS="-O2 -Wall -march=native" ./configure
make


But how can I compile it in 32 bit?

---

### Post by sotiris2 on 2015-09-18
Try replacing native in > [COLOR=#000000]CFLAGS="-O2 -Wall -march=native" ./configure with m32[/COLOR]

---

### Post by Tony T on 2015-09-18
> **sotiris2 said:**
> Try replacing native in  with m32

Thank you, I'll give it a try and report back.

---

### Post by Tony T on 2015-09-18
No It did not work :-(

Here is what I get:
> checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking whether make supports nested variables... (cached) yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... no
configure: error: in `/home/tony/Downloads/sgminer':
configure: error: C compiler cannot create executables

---

### Post by sotiris2 on 2015-09-18
I made a mistake -m32 is actually a distinct argument rather than an option for -march so you probably need to replace the whole -march=native bit with -m32. Or pick an option representing your target cpu. Have a look [here](https://gcc.gnu.org/onlinedocs/gcc-4.9.3/gcc/i386-and-x86-64-Options.html).

---

### Post by Tony T on 2015-09-19
Thanks sotiris2c for your help, but I still can't get it to compile in 32 bit. I've  tried  many variations of CFLAGS="-m32 -Wall -std=gnu99" ./configure to  no avail. I'm going to give it a rest for now. Thanks again!

---

