---
title: "gcc can not create executables?"
date: 2005-05-27
forum: General Help
---

### Post by vehyla on 2005-05-27
Earlier today my computer stopped having the ability to create gcc executables.  Anything that I run a ./configure on fails with this message:

checking for gcc... gcc
checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.

This feature used to run fine however today I did an "apt-get upgrade" and every since then I can not run ./configure on anything.  Also if I try to manually compile something with "gcc -o gui gui.c" it scrolls errors down the screen.  There errors pretty much have a file then say "(first use in this function)" for example:
gui.c:1328: error: `XtPointer' undeclared (first use in this function)
gui.c:1328: error: syntax error before numeric constant
gui.c:1339: error: `Boolean' undeclared (first use in this function)
gui.c:1339: error: syntax error before "ClusterGenes"
gui.c:1345: error: syntax error before "widget"
gui.c:1354: error: `button' undeclared (first use in this function)
gui.c:1355: error: `ClusterGenes' undeclared (first use in this function)
gui.c:1357: error: `ClusterArrays' undeclared (first use in this function)

Also if this helps anyone this is the config.log from a ./configure I tried.  It resembles all the config.log files from other things I have already compiled but reran ./configure to see what would happen:
echelon:~/Desktop/printtool-4.5> cat config.log                               [13:38]
This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

configure:556: checking for a BSD compatible install
configure:609: checking whether build environment is sane
configure:666: checking whether make sets ${MAKE}
configure:712: checking for working aclocal
configure:725: checking for working autoconf
configure:738: checking for working automake
configure:751: checking for working autoheader
configure:764: checking for working makeinfo
configure:781: checking for gcc
configure:894: checking whether the C compiler (gcc  ) works
configure:910: gcc -o conftest    conftest.c  1>&5
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../crt1.o: file not recognized: File format not recognized
collect2: ld returned 1 exit status
configure: failed program was:

#line 905 "configure"
#include "confdefs.h"

main(){return(0);}


I'm surprised this can happen from just an upgrade but I can't think of anything else.  Any ideas?

---

### Post by rum beverage on 2005-05-27
the thread posted right before this one talks about the same issue.  i just checked and it's already been patched.  just load up synaptic...reload and upgrade binutils

---

### Post by lorap on 2005-05-30
hi buddy!
try "cc".
it's a native unix  c compiler.
to compile, just compile write this:

cc -c file.c

this'll produce an object file.
to create an executable write this:

cc -o file file.c

this'll create an executable "file".
have a nice day.
pavel

---

### Post by vehyla on 2005-06-01
[QUOTE=rum beverage]the thread posted right before this one talks about the same issue.  i just checked and it's already been patched.  just load up synaptic...reload and upgrade binutils[/QUOTE]
 Must have missed that thread.  
lorap: I tried cc and that had the same results.
rum beverage: Thanks for the info.  A quick upgrade to binutils and all was well.

---

