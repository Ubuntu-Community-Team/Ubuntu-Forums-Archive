---
title: "compiling does not work"
date: 2007-02-10
forum: General Help
---

### Post by Ossipon on 2007-02-10
I tried to compile the latest vlc player from source, but ./configure got me the following output:

```
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for gcc... gcc
checking for C compiler default output file name...
configure: error: C compiler cannot create executables
See `config.log' for more details.
```

The relevant part of config.log looked like this:

```
configure:3359: checking for C compiler default output file name
configure:3386: gcc   -L/opt/local/lib conftest.c  >&5
/lib/libc.so.6: file not recognized: File format not recognized
collect2: ld returned 1 exit status
configure:3389: $? = 1
configure:3427: result:
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "vlc"
| #define PACKAGE_TARNAME "vlc"
| #define PACKAGE_VERSION "0.8.6a"
| #define PACKAGE_STRING "vlc 0.8.6a"
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "vlc"
| #define VERSION "0.8.6a"
| /* end confdefs.h.  */
|
| int
| main ()
| {
|
|   ;
|   return 0;
| }
configure:3434: error: C compiler cannot create executables
See `config.log' for more details.
```

The only help I found on google told me to install build-essential, gcc, binutils etc. , but I have all of those already. I also tried to reinstall them and dpkg-reconfigure them.
Then I tried to compile a simple hello world program. It showed the following error:

```
gcc -v hello-world.c
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release x86_64-linux-gnu
Thread model: posix
gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)
 /usr/lib/gcc/x86_64-linux-gnu/4.1.2/cc1 -quiet -v hello-world.c -quiet -dumpbase hello-world.c -mtune=generic -auxbase hello-world -version -fstack-protector -fstack-protector -o /tmp/ccWMSIvZ.s
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../x86_64-linux-gnu/include"
ignoring nonexistent directory "/usr/include/x86_64-linux-gnu"
#include "..." search starts here:
#include <...> search starts here:
 /usr/local/include
 /usr/lib/gcc/x86_64-linux-gnu/4.1.2/include
 /usr/include
End of search list.
GNU C version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5) (x86_64-linux-gnu)
        compiled by GNU C version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5).
GGC heuristics: --param ggc-min-expand=64 --param ggc-min-heapsize=63731
Compiler executable checksum: 69b037dea6ceacffa2e97527b1ac3ca3
 as -V -Qy -o /tmp/ccCWRgDR.o /tmp/ccWMSIvZ.s
GNU assembler version 2.17 (x86_64-linux-gnu) using BFD version 2.17 Debian GNU/Linux
 /usr/lib/gcc/x86_64-linux-gnu/4.1.2/collect2 --eh-frame-hdr -m elf_x86_64 -dynamic-linker /lib64/ld-linux-x86-64.so.2 /usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64/crt1.o /usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64/crti.o /usr/lib/gcc/x86_64-linux-gnu/4.1.2/crtbegin.o -L/usr/lib/gcc/x86_64-linux-gnu/4.1.2 -L/usr/lib/gcc/x86_64-linux-gnu/4.1.2 -L/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64 -L/lib/../lib64 -L/usr/lib/../lib64 /tmp/ccCWRgDR.o -lgcc --as-needed -lgcc_s --no-as-needed -lc -lgcc --as-needed -lgcc_s --no-as-needed /usr/lib/gcc/x86_64-linux-gnu/4.1.2/crtend.o /usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64/crtn.o
/lib/libc.so.6: file not recognized: File format not recognised
collect2: ld returned 1 exit status
```

I'm using kubuntu 6.10 on an AMD64 architecture. I'm not able to compile anything so any help would be greatly appreciated.

---

### Post by linuchsan on 2007-02-10
Did you do apt-get build-essential to get your building tools?

---

### Post by Ossipon on 2007-02-10
Well, actually, I did apt-get install build-essential, I also did apt-get --reinstall install build essential and dpkg-reconfigure build-essential

---

### Post by pay on 2007-02-10
You could try this repository for a prebuilt vlc ```
http://packages.freecontrib.org/ubuntu/plf/ edgy-plf free non-free
```Also ```
sudo apt-get build-dep vlc
``` to make sure that you have the dependencies.

---

### Post by Ossipon on 2007-02-11
```
sudo apt-get build-dep vlc
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Build-dependencies for vlc could not be satisfied.
```

I already have vlc installed from the repositories, but it crashes when I use IPTV, that's why I tried to compile the newest SVN snapshot. For me, it also works to downgrade vlc to the dapper version.

But the problem here is that I'm not able to compile anything, not even an hello world program, so even if I can use vlc another way, it's possible that I need to compile something else tomorrow.

---

### Post by Tesiph on 2007-02-20
I had the same problem. Are you using mixed repositories?

My problem was that half of build-essential dependencies were from edgy, and the rest from feisty. After I updated all build-essential dependencies to feisty, the problem was gone.

---

### Post by Ossipon on 2007-03-15
It works!

I wasn't using mixed repositories before, but I upgraded all the dependencies to feisty and that did it. I just hope that it's nog going to give trouble with other edgy packages.

---

