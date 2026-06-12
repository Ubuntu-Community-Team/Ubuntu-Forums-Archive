---
title: "link with libc_p.a causes floating exception"
date: 2008-02-19
forum: General Help
---

### Post by pember on 2008-02-19
I posted this as a bug but thought I'd post here too.
=======================================================
I'm trying to profile a code that's I/O intensive and so I would like to
use the profiling version of the C library, libc_p.a. In a nutshell, executables
compiled with gcc with -p (or -pg) and linked with libc_p.a have a floating
point exception right out the gate. (I also have the Intel C compiler installed,
icc, and the same is true.)

This is true for all versions of gcc I have installed, except for 2.95, for
which the link fails.

For (the simplest) example:

-------------------------------------------------------------------------
%coot 108: cat hello.c
#include <stdio.h>

main() {

  printf ("hello, world!\n");

}
%coot 109: gcc hello.c
%coot 110: a.out
hello, world!
%coot 111: gcc hello.c -lc_p
%coot 112: a.out
hello, world!
%coot 113: gcc -p hello.c -lc_p
%coot 114: a.out
Floating exception
%coot 115: gcc -p hello.c
%coot 116: a.out
hello, world!
%coot 117: gcc -pg hello.c
%coot 118: a.out
hello, world!
%coot 119: gcc -p hello.c -lc_p
%coot 120: a.out
Floating exception
%coot 121: gcc -pg hello.c -lc_p
%coot 122: a.out
Floating exception
%coot 123: gcc-3.3 -pg hello.c -lc_p
%coot 124: a.out
Floating exception
%coot 125: gcc-3.4 -pg hello.c -lc_p
%coot 126: a.out
Floating exception
%coot 127: gcc-4.2 -pg hello.c -lc_p
%coot 128: a.out
Floating exception
%coot 129: gcc-2.95 hello.c
%coot 130: a.out
hello, world!
%coot 131: gcc-2.95 -pg hello.c
%coot 132: a.out
hello, world!
%coot 133: gcc-2.95 -pg hello.c -lc_p
/usr/bin/../lib/libc_p.a(syslog.op): In function `__vsyslog_chk':
(.text+0x70e): undefined reference to `_Unwind_Resume'
(blah-blah-blah)
%coot 134:
--------------------------------------------------------------------------

I'm using the version of libc_p.a found in the Synaptic Package manger (SPM) under libc6-prof.
The versions of gcc were also found under the SPM.

I found in the Synaptic Package manger (SPM) under libc6-prof.

I've also installed gcc in the same way. Under the SPM, versions 2.95,
3.3., 3.4, 4.1, and 4.2 are available. The base version is 4.1:

-----------------------------------------
%coot 104: gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
%coot 105:
-----------------------------------

I have a neighbor running Red Hat with gcc 3.2.3, and I am able to build and run there, so I know I'm otherwise "doing the right thing:"
-----------------------------------------------------------------------------------------------------------------------------------------------
[pember@tern _gprof]$ gcc -p hello.c -lc_p
[pember@tern _gprof]$ ./a.out
hello, world!
[pember@tern _gprof]$
-----------------------------------------------------------------------------------------------------------------------------------------------

Other info:
----------------------------------------------------------------------
%coot 134: cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"
%coot 136: dpkg -l gcc | cat
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name Version Description
+++-==============-================-============================================
ii gcc 4:4.1.2-9ubuntu2 The GNU C compiler
%coot 137: dpkg -l gcc-3.3 | cat
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name Version Description
+++-==============-=================-============================================
ii gcc-3.3 1:3.3.6-15ubuntu2 The GNU C compiler
%coot 138: dpkg -l gcc-3.4 | cat
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name Version Description
+++-==============-==============-============================================
ii gcc-3.4 3.4.6-6ubuntu2 The GNU C compiler
%coot 139: dpkg -l gcc-4.1 | cat
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name Version Description
+++-==============-===============-============================================
ii gcc-4.1 4.1.2-16ubuntu2 The GNU C compiler
%coot 140: dpkg -l gcc-4.2 | cat
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name Version Description
+++-==============-==============-============================================
ii gcc-4.2 4.2.1-5ubuntu4 The GNU C compiler
%coot 143: dpkg -l libc6-prof
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name Version Description
+++-=======================-=======================-==============================================================
ii libc6-prof 2.6.1-1ubuntu10 GNU C Library: Profiling Libraries
------------------------------------------------------------------------------------------------------

Thanks,
Rick Pember

---

