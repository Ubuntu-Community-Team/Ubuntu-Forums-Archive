---
title: "installing older version of gcc and and adding path variables"
date: 2006-11-24
forum: General Help
---

### Post by jaind on 2006-11-24
I have come across a simple (but important) problem which is holding up my work.
I would really appreciate if you can help me sort the problem which i describe below:

I am using ubuntu6.10 version with gcc4.1.1 installed. i need to install an older version of gcc (3.1). however after i unistall gcc 4.1.1 and install gcc3.1 and run "./configure" on a software i have, i am getting the following error:
"configure: error: no acceptable C compiler found in $PATH"

Now i know think i know how to add the PATH variable(as i understand i have to cd to /root and add the path in the .bashrc file using export command). however i do not know what path to add. i tried "bin/gcc" among others but it didnt work.

It would be great if you can help me on this.

Thanks for your help!

~jaind

---

### Post by taurus on 2006-11-24
See if you really have gcc on your system...

```
gcc -v
```

---

### Post by jaind on 2006-11-25
by using command gcc-v i get the following output:
gcc: command not found

I went to the synaptic package manager and installed "gcc 3.3.6-13 ubuntu2 ". but its still showing the same message. i dont know what is wrong.

Thanks!

PS: as an aside: i tried to install gcc 3.3.6 by downloading from one of the mirrors. however the instillation instructions at the gcc webpage names a gazillion options i have to give, which i was unsure of so i had used the synaptic package manager instead.
is installing gcc on your own really so complicated?

---

### Post by taurus on 2006-11-25
There is a space between c and -, gcc -v...

---

### Post by jaind on 2006-11-25
sorry. it was a typo in my post. i did use "gcc -v". so my problem still holds (:

Thanks!

---

### Post by taurus on 2006-11-25
Are you sure you did install "gcc 3.3.6-13 ubuntu2" from synaptic?  Better open synaptic again and check it...

---

### Post by jaind on 2006-11-25
the synaptic package manager does say that i have "gcc3.3.6-13ubuntu2  The GNU C Compiler" installed(its tagged green).

I also ran "updatedb" as root and checked "gcc -v" again, with the same "gcc: Command not found" error.

Thanks!

---

### Post by taurus on 2006-11-25
Run this command from a terminal.

```
find / -name gcc* -print
-or-
locate gcc*
```
Maybe it's called gcc-3.3.6 instead of gcc!!!

---

### Post by jaind on 2006-11-25
1) I ran: "gcc-3.3 --version" and got the following output:

gcc-3.3 (GCC) 3.3.6 (Ubuntu 1:3.3.6-13ubuntu2)
Copyright (C) 2003 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

2) I ran "locate gcc*" and got a huge number of lines, some of which are as below:
------------------------------------------------------------------
/lib/libgcc_s.so.1
/usr/bin/gcc-3.3
/usr/bin/gccbug-3.3
/usr/bin/gccmakedep
/usr/bin/i486-linux-gnu-gcc-3.3
/usr/lib/gcc
/usr/lib/gcc/i486-linux-gnu
/usr/lib/gcc/i486-linux-gnu/4.1.2
/usr/lib/gcc/i486-linux-gnu/4.1.2/cc1
/usr/lib/gcc/i486-linux-gnu/3.4.6
/usr/lib/gcc/i486-linux-gnu/3.4.6/cc1
/usr/lib/openoffice/program/libcomphelp4gcc3.so
/usr/lib/openoffice/program/libcppuhelpergcc3.so.3
/usr/lib/openoffice/program/libgcc3_uno.so
/usr/lib/openoffice/program/libi18nisolang1gcc3.so
/usr/lib/openoffice/program/libi18nregexpgcc3.so
/usr/lib/openoffice/program/libi18nutilgcc3.so
/usr/lib/openoffice/program/libjvmaccessgcc3.so.3
/usr/lib/openoffice/program/libsalhelpergcc3.so.3
/usr/lib/openoffice/program/libucbhelper3gcc3.so
/usr/lib/openoffice/program/libuno_cppuhelpergcc3.so.3
/usr/lib/openoffice/program/libuno_salhelpergcc3.so.3
/usr/lib/openoffice/program/libvos3gcc3.so
/usr/lib/libgccpp.so.1
/usr/lib/libgccpp.so.1.0.2
/usr/lib/libstlport_gcc.so.4.6
/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libjavaplugin_nscp_gcc29.so
/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/plugin/i386/ns7-gcc29
/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
/usr/lib/gcc-lib
/usr/lib/gcc-lib/i486-linux-gnu
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/iso646.h
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/README
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/float.h
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/limits.h
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/stdarg.h
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/stdbool.h
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/stddef.h
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/syslimits.h
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/unwind.h
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/varargs.h
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/asm
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/asm/posix_types.h
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/mmintrin.h
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/emmintrin.h
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/pmmintrin.h
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/xmmintrin.h
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/cc1
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/collect2
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/specs
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/libgcc.a
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/libgcc_eh.a
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/crtbegin.o
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/crtbeginS.o
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/crtbeginT.o
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/crtend.o
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/crtendS.o
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/libgcc_s.so
/usr/share/doc/gcc-3.3-base
/usr/share/doc/gcc-3.3-base/README.Debian
/usr/share/doc/gcc-3.3-base/TODO.Debian
/usr/share/doc/gcc-3.3-base/changelog.Debian.gz
/usr/share/doc/gcc-3.3-base/changelog.gz
/usr/share/doc/gcc-3.3-base/copyright
/usr/share/doc/gcc-3.3-base/README.Bugs
/usr/share/doc/gcc-3.3-base/gcc
/usr/share/doc/gcc-3.3-base/gcc/changelog.gz
/usr/share/doc/gcc-3.3-base/NEWS.html
/usr/share/doc/gcc-3.3-base/NEWS.gz
/usr/share/doc/gcc-3.3-base/test-summary.gz
/usr/share/doc/gcc-3.3-base/FAQ.gz
/usr/share/doc/gcc-4.1-base
/usr/share/doc/gcc-4.1-base/.changelog.Debian.gz
/usr/share/doc/gcc-4.1-base/.copyright
/usr/share/doc/gcc-4.1-base/README.Debian.gz
/usr/share/doc/gcc-4.1-base/TODO.Debian
/usr/share/doc/gcc-4.1-base/changelog.Debian.gz
/usr/share/doc/gcc-4.1-base/changelog.gz
/usr/share/doc/gcc-4.1-base/copyright
/usr/share/doc/gcc-3.4-base
/usr/share/doc/gcc-3.4-base/README.Debian.gz
/usr/share/doc/gcc-3.4-base/NEWS.Debian.gz
/usr/share/doc/gcc-3.4-base/TODO.Debian
/usr/share/doc/gcc-3.4-base/copyright
/usr/share/doc/gcc-3.4-base/changelog.gz
/usr/share/doc/gcc-3.4-base/changelog.Debian.gz
/usr/share/doc/gcc-3.3
/usr/share/doc/libgcc1
/usr/share/lintian/overrides/libgcc1
/usr/share/locale-langpack/en_GB/LC_MESSAGES/gcc-3.3.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/gcc-3.4.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/gcc-4.0.mo
/usr/share/man/man1/gccbug-3.3.1.gz
/usr/share/man/man1/gcc-3.3.1.gz
/usr/share/man/man1/gccmakedep.1x.gz
/usr/share/man/man1/i486-linux-gnu-gcc-3.3.1.gz
/usr/share/man/man7/fsf-funding.7gcc.gz
/usr/share/man/man7/gfdl.7gcc.gz
/usr/share/man/man7/gpl.7gcc.gz
/usr/src/linux-headers-2.6.17-10/include/acpi/platform/acgcc.h
/usr/src/linux-headers-2.6.17-10/include/asm-ia64/gcc_intrin.h
/usr/src/linux-headers-2.6.17-10/include/linux/compiler-gcc.h
/usr/src/linux-headers-2.6.17-10/include/linux/compiler-gcc3.h
/usr/src/linux-headers-2.6.17-10/include/linux/compiler-gcc4.h
/usr/src/linux-headers-2.6.17-10/scripts/gcc-version.sh
/usr/src/linux-headers-2.6.17-10-generic/include/linux/compiler-gcc.h
/usr/src/linux-headers-2.6.17-10-generic/include/linux/compiler-gcc3.h
/usr/src/linux-headers-2.6.17-10-generic/include/linux/compiler-gcc4.h
/usr/src/linux-headers-2.6.17-10-generic/scripts/gcc-version.sh
-------------------------------------

-- so i think i have "gcc-3.3" :)

-- now back to the original problem, which i describe again below:
when i do ./configure on a software, i get the following error message:
"configure: error: no acceptable C compiler found in $PATH"

how do i find the correct path??

Thanks a ton for your help!!

---

### Post by taurus on 2006-11-25
Well, you can link gcc to gcc-3.3...  Open a terminal and do

```
cd /usr/bin
sudo ln -s gcc-3.3 gcc
gcc -v
```

---

### Post by jaind on 2006-11-25
I was able to link gcc and gcc3.3.
A couple of Q's:

1) i added the following lines to the ".bashrc" file in /root
PATH=$PATH:/usr/bin/gcc-3.3
export PATH

-- but im not sure if this is the correct path?

2) I got the following (new) error when i ran the ./configure again after i linked up gcc and gcc3.3

---------------------------------------------------
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
---------------------------------------------------------------

I dont know what is wrong. i had unistalled "gcc4.1.1" before i installed "gcc3.3.6-13 ubuntu2". 
--Also, the synaptic package manager shows that i have "3.3.6-13ubuntu2 The GNU C preprocessor installed"

Thanks!

---

### Post by taurus on 2006-11-25
That is not how you add a path to PATH!!!  Your PATH should look something like this

```
PATH=$PATH:/usr/bin
```
but not

```
PATH=$PATH:/usr/bin/gcc-3.3
```
And since you decided to install gcc-3-3.6 by hand, you need to go back to synaptic and install g++-3.3.6, c++-3.3.6, etc....

---

### Post by jaind on 2006-11-25
oops!! sorry for that. im new to linux!

I did install gcc with the synaptic package manager(and not by hand). However, ive gone ahead and installed the  "g++-3.3" compiler(using synaptic). i also linked up "g++-3.3" to "g++". 

how do i install "c++-3.3.6"? i searched for "c++" in synaptic but am not sure what im looking for.

-- do i have to install some other things also? it would be great if you can give a list of them.

Thank you!!

---

### Post by taurus on 2006-11-25
Try to run ./configure again to see what happens now because I don't know what other apps it needs...  You just have to install each one when the program complains about not finding something then.

I guess your program wouldn't compile with the latest version of gcc!

---

### Post by jaind on 2006-11-25
i was able to run the ./configure and make and make install!!

yippes!!

Thanks a ton for your help!!

---

### Post by jaind on 2006-11-25
one last Q :rolleyes: 

1) i might need to install one of the gcc versions which are not there in the synaptic package manager. i can get the software from the mirrors, but the documentation to install looked really scary(there were so many options, etc.). 
--is there an easy way?

---

### Post by taurus on 2006-11-25
> **jaind said:**
> one last Q :rolleyes: 

1) i might need to install one of the gcc versions which are not there in the synaptic package manager. i can get the software from the mirrors, but the documentation to install looked really scary(there were so many options, etc.). 
--is there an easy way?
Which version of gcc do you need now?  If you tell me where it is, maybe I can have a look and tell you how to build it!!!  Can't promise anything but will look into it if I get a chance...  ;)

---

### Post by jaind on 2006-11-25
Hi,

I dont know which version of gcc the software will compile with so im just trying the hit-and-trail method. 

The software didnt work with gcc-3.3 so im trying gcc-2.95 instead. I installed it from the synaptic package manager. 
Now im trying to link gcc-2.95 with gcc with the method you told me as:
cd /usr/bin
sudo ln -s gcc-2.95 gcc

However, this linking doesnt work and i get the following:
ln: creating symbolic link `gcc' to `gcc-2.95': File exists

-- i probably have to delete the old symbolic link but i dont know how to find it and delete it.

I dont know what to do now. :(

---

