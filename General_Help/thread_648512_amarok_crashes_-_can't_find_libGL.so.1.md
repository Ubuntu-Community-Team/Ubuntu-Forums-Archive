---
title: "amarok crashes - can't find libGL.so.1"
date: 2007-12-23
forum: General Help
---

### Post by insert_name_here on 2007-12-23
When I try to start Amarok, it (just recently, after uninstalling fglrx and switching to the Mesa driver) it doesn't start, saying:

$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
amarokapp: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

However, libGL.so.1 exists in /usr/lib

---

### Post by ed-koala on 2007-12-23
I looked into this on the web, and it might be a package install issue.  This page [http://packages.debian.org/etch/amarok]("http://packages.debian.org/etch/amarok") lists all the dependencies of Amarok, and one in particular you should check on is libgl1-mesa-glx.  Try reinstalling that one, and others, to see if that solves your problem  :)

---

### Post by insert_name_here on 2007-12-23
Bingo!  We're in business.

Thanks

---

