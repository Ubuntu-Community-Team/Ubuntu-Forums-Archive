---
title: "gdb 7.6 in Precise"
date: 2013-08-09
forum: General Help
---

### Post by james_mcl on 2013-08-09
I've recently installed gcc 4.8 from the Toolchain repository ([https://launchpad.net/~ubuntu-toolchain-r/+archive/test](https://launchpad.net/~ubuntu-toolchain-r/+archive/test)), and have noticed that when I compile with -g, the debugging symbols aren't compatible with gdb 7.4. I have to compile with

-g -gdwarf-2

instead, to get the symbols in an older format which is compatible.

Since I'd like to see if this newer format provides more information than DWARF v2, I've downloaded gdb 7.6 from gnu.org. Before I uninstall 7.4 and set about compiling it, could anyone who's compiled it for use on their Precise box advise me of any pitfalls they encountered or potential issues?

---

### Post by james_mcl on 2013-08-09
Decided I was being overcautious, and installed it anyway.

```

CC="gcc-4.8" CXX="g++-4.8" ./configure
CC="gcc-4.8" CXX="g++-4.8" make
sudo CC="gcc-4.8" CXX="g++-4.8" make install

```

All seems fine, except that I don't remember if the package-manager-supplied version of gdb used to output the following message:

```

warning: no loadable sections found in added symbol-file system-supplied DSO at 0x7fffa7dfe000

```

(this occurred after I wrote a short script in C++ to trigger a core dump for test purposes).
As I said, gdb seems to be working fine otherwise, but just wondered if anyone else was getting that?
------------------------------------
EDIT: After I did this, the package manager version of valgrind (3.7.0) started crashing whenever I tried to use it. I uninstalled it, and installed 3.8.1 from valgrind.org - which solved the problem.

---

