---
title: "qtella-0.6.5"
date: 2005-04-28
forum: General Help
---

### Post by bobgreen5s on 2005-04-28
Hello I am trying to install a p2p application called qtella-0.6.5 . When I do ./configure in the directory this is what happens, 
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/bobgreen5s/Downloads/qtella-0.6.5/missing: Unknown `--run' option
Try `/home/bobgreen5s/Downloads/qtella-0.6.5/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for Qt moc...
[b]Qt's moc not found! If you have installed Qt in an
unusual place, please use the "--with-qt-moc=" option[/b]
```

I have heard that this is because my qt is too old or something but I don't really know what that means. Can this be fixed?

Any help is appreciated.

---

### Post by DJ_Max on 2005-04-28
What version do you have? The error is more then likely you not having the development binaries.
If you have libqt3, you will need libqt3-dev & qt3-dev-tools

---

### Post by bobgreen5s on 2005-04-28
Thank you, I installed those packages and got a little further, this was my error message:

```
checking for Qt moc... found in /usr/bin
checking for Qt uic... found in /usr/bin
checking for Qt libraries...
[B]Qt libs not found! If you have installed Qt in an
unusual place, please use the "--with-qt-libs=" option[/B]

```

:(

---

### Post by DJ_Max on 2005-04-28
[QUOTE=bobgreen5s]Thank you, I installed those packages and got a little further, this was my error message:

```
checking for Qt moc... found in /usr/bin
checking for Qt uic... found in /usr/bin
checking for Qt libraries...
[B]Qt libs not found! If you have installed Qt in an
unusual place, please use the "--with-qt-libs=" option[/B]

```

:([/QUOTE]
 Sure it's the same problem, need certain dev packages

---

