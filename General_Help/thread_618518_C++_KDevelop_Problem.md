---
title: "C++ KDevelop Problem"
date: 2007-11-20
forum: General Help
---

### Post by paul007 on 2007-11-20
Hi everyone...

I am a newbie in Ubuntu. I have the latest version(7.10).

I try to write a very simple problem in KDevelop in C++ and i face some problems!!!

When i was trying to build the program Hello World i see this message:
[I]/home/pavlos/Desktop/HelloWorld/debug
There is no Makefile in this directory
and no configure script for this project.
Run automake & friends and configure first?[/I]

I push the button Run Them and and i saw another message:
[I]cd '/home/pavlos/Desktop/HelloWorld' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && mkdir '/home/pavlos/Desktop/HelloWorld/debug' && cd '/home/pavlos/Desktop/HelloWorld/debug' && CXXFLAGS="-O0 -g3" "/home/pavlos/Desktop/HelloWorld/configure" --enable-debug=full && cd '/home/pavlos/Desktop/HelloWorld/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
aclocal
make: aclocal: Command not found
make: *** [all] Error 127
*** Exited with status: 2 ***[/I]

Do you have any idea about the solution of the problem?

What can i do now?

---

### Post by cmnorton on 2007-11-20
Do you have build-essentials installed? Basically, use Synaptic manager, and see if this package is installed.

---

### Post by eqo314 on 2007-12-13
same issue, i do have build essentials installed.

---

