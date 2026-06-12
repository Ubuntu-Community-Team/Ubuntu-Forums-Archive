---
title: "Valgrind fatal error strlen"
date: 2013-03-22
forum: General Help
---

### Post by Nicilled on 2013-03-22
I need help to fix this problem:

==14431== Memcheck, a memory error detector
==14431== Copyright (C) 2002-2011, and GNU GPL'd, by Julian Seward et al.
==14431== Using Valgrind-3.7.0 and LibVEX; rerun with -h for copyright info
==14431== Command: ./uloha 3999
==14431== 


valgrind:  Fatal error at startup: a function redirection
valgrind:  which is mandatory for this platform-tool combination
valgrind:  cannot be set up.  Details of the redirection are:
valgrind:  
valgrind:  A must-be-redirected function
valgrind:  whose name matches the pattern:      strlen
valgrind:  in an object with soname matching:   ld-linux-x86-64.so.2
valgrind:  was not found whilst processing
valgrind:  symbols from the object with soname: ld-linux-x86-64.so.2
valgrind:  
valgrind:  Possible fixes: (1, short term): install glibc's debuginfo
valgrind:  package on this machine.  (2, longer term): ask the packagers
valgrind:  for your Linux distribution to please in future ship a non-
valgrind:  stripped ld.so (or whatever the dynamic linker .so is called)
valgrind:  that exports the above-named function using the standard
valgrind:  calling conventions for this platform.  The package you need
valgrind:  to install for fix (1) is called
valgrind:  
valgrind:    On Debian, Ubuntu:                 libc6-dbg
valgrind:    On SuSE, openSuSE, Fedora, RHEL:   glibc-debuginfo
valgrind:  
valgrind:  Cannot continue -- exiting now.  Sorry.

I have libc6-dbg installed and libc6-dbg:i386 too. Searched this problem on google but nothing helps. I am running on crungbang, that is linux based on debian.

---

