---
title: "Can't compile crosstool"
date: 2007-08-22
forum: General Help
---

### Post by scorpio2002 on 2007-08-22
Hi there!
I0m struggling to compile crosstool on my ubuntu system. Basically, the compilation fails with the following errors:

```

In file included from version.c:33:
/home/skorpio/crosstool-0.43/build/powerpc-405-linux-gnu/gcc-4.1.0-glibc-2.3.6/build-glibc/csu/version-info.h:2:1: [COLOR="Red"]missing terminating " character[/COLOR]
/home/skorpio/crosstool-0.43/build/powerpc-405-linux-gnu/gcc-4.1.0-glibc-2.3.6/build-glibc/csu/version-info.h:3:1: [COLOR="Red"]missing terminating " character[/COLOR]
make[2]: *** [/home/skorpio/crosstool-0.43/build/powerpc-405-linux-gnu/gcc-4.1.0-glibc-2.3.6/build-glibc/csu/version.o] Error 1
make[2]: Leaving directory `/home/skorpio/crosstool-0.43/build/powerpc-405-linux-gnu/gcc-4.1.0-glibc-2.3.6/glibc-2.3.6/csu'
make[1]: *** [csu/subdir_lib] Error 2
make[1]: Leaving directory `/home/skorpio/crosstool-0.43/build/powerpc-405-linux-gnu/gcc-4.1.0-glibc-2.3.6/glibc-2.3.6'
make: *** [lib] Error 2
```

What kind of issue is this ?!?

---

### Post by scorpio2002 on 2007-08-23
Nobody does cross-compiling on ubuntu?

---

### Post by LeeTL1220 on 2007-08-23
I am having the exact same issue.  So at least 2 people are cross compiling (to the PPC 405, no less!)  on Ubuntu.

I switched my shell to zsh (as per a suggestion elsewhere on the Internet, sorry that I do not have a citation), but that did not work.

---

### Post by scorpio2002 on 2007-08-23
I tried to contact the author, but he's too busy, I don't think I'll get an answer from him. Anyway, compilation works fine on my fedora box, it's ubuntu that's giving a lot of problems with this.

A solution could be to use qemu to create a virtual ppc machine and to install a copy of linux on it so you won't need crosstool... it seems the only solution if you want to cross compile on ubuntu.

---

### Post by scorpio2002 on 2007-08-23
Just to list a few things I tried:

 - installed gawk instead of mawk (seems that gcc has got some problems with mwak)
-  changed shell from sh to bash
-  changed the target architecture from 750 to 405

---

### Post by scorpio2002 on 2007-08-24
It seems that ubuntu has problems with qemu-ppc too -.- Basically, I can't start the virtual machine because there are some files missing. 
Unfortunatelly, Ubuntu seems not redy for cross-compiling / ppc virtualization... hope canonical will do something about that.

For this issues, use Fedora 7, which works quite well and out of the box with qemu-virtualization and crosstool.

---

### Post by peiworld on 2008-06-13
I have the same problem...but here is the solution I found.

The problem:
"Compiled on a Linux >>2.6.24-18-generic<< system on 2008-06-13.\n"
"Available extensions:
"
"	GNU libio by Per Bothner\n"
"	crypt add-on version 2.1 by Michael Glad and others\n"
"	linuxthreads-0.10 by Xavier Leroy\n"
"	BIND-8.2.3-T5B\n"
"	libthread_db work sponsored by Alpha Processor Inc\n"
"	NIS(YP)/NIS+ NSS modules 0.19 by Thorsten Kukuk\n"
"	software FPU emulation by Richard Henderson, Jakub Jelinek and others\n"

as the error message said, line 2 and 3 is missing " character.

to fix it, you will need to a Makefile in glibc.2.3.6/csu/ directory, and repack it to replace the downloaded one. below is the change...

From
"\"Available extensions:\\n\""

to

"\"Available extensions:\""

or patch your file before you repack it back to .bz2

Patch file:
============================================================================
--- glibc-2.3.6/csu/Makefile	2008-06-13 15:23:28.000000000 +1000
+++ glibc-2.3.6-new/csu/Makefile	2008-06-13 15:07:33.000000000 +1000
@@ -241,7 +241,7 @@
 	 esac; \
 	 files="$(all-Banner-files)";				\
 	 if test -n "$$files"; then				\
-	   echo "\"Available extensions:\\n\"";			\
+	   echo "\"Available extensions:\"";			\
 	   sed -e '/^#/d' -e 's/^[[:space:]]*/	/'		\
 	       -e 's/^\(.*\)$$/\"\1\\n\"/' $$files;		\
 	 fi) > $@T
============================================================================

---

