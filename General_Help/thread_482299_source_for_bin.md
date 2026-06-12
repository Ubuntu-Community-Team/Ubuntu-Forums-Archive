---
title: "source for /bin"
date: 2007-06-23
forum: General Help
---

### Post by jasonlfunk on 2007-06-23
Where could I find the source files for the files in /bin such as ls, echo, chown, etc?

---

### Post by WW on 2007-06-23
First, find the package that provides the command.  You can use the **dpkg -S** command. For example,
```

$ [color=blue]dpkg -S /bin/ls[/color]
coreutils: /bin/ls
$

```
So the command /bin/ls is provided by the package **coreutils**.

To get the source code for a package, use **apt-get source**. (You will need to have the source repository enabled in /etc/apt/sources.list.)  For example,
```

~/source$ [color=blue]apt-get source coreutils[/color]   # Get the source code from the Ubuntu repository
Reading package lists... Done
Building dependency tree... Done
Need to get 4931kB of source archives.
Get:1 http://ca.archive.ubuntu.com dapper/main coreutils 5.93-5ubuntu4 (dsc) [845B]
Get:2 http://ca.archive.ubuntu.com dapper/main coreutils 5.93-5ubuntu4 (tar) [4885kB]
Get:3 http://ca.archive.ubuntu.com dapper/main coreutils 5.93-5ubuntu4 (diff) [4 5.9kB]
Fetched 4931kB in 55s (88.2kB/s)
dpkg-source: extracting coreutils in coreutils-5.93
dpkg-source: unpacking coreutils_5.93.orig.tar.gz
dpkg-source: applying ./coreutils_5.93-5ubuntu4.diff.gz
~/source$ [color=blue]ls[/color]
coreutils-5.93                   coreutils_5.93-5ubuntu4.dsc
coreutils_5.93-5ubuntu4.diff.gz  coreutils_5.93.orig.tar.gz
~/source$ [color=blue]cd coreutils-5.93[/color]
~/source/coreutils-5.93$ [color=blue]ls[/color]
coreutils-5.93  coreutils-5.93.tar.bz2  coreutils-5.93.tar.bz2.sig  debian
~/source/coreutils-5.93$ [color=blue]tar xjf coreutils-5.93.tar.bz2[/color]   # Extract the tar file
~/source/coreutils-5.93$ [color=blue]cd coreutils-5.93/[/color]
~/source/coreutils-5.93/coreutils-5.93$ [color=blue]ls[/color]
ABOUT-NLS     configure.ac  Makefile.cfg    src
aclocal.m4    COPYING       Makefile.in     tests
announce-gen  doc           Makefile.maint  THANKS
AUTHORS       GNUmakefile   man             THANKS-to-translators
build-aux     INSTALL       NEWS            THANKStt.in
ChangeLog     lib           old             TODO
config.hin    m4            po
configure     Makefile.am   README
~/source/coreutils-5.93/coreutils-5.93$ [color=blue]cd src[/color]
~/source/coreutils-5.93/coreutils-5.93/src$ [color=blue]ls ls*[/color]  # We're now in the source directory
ls.c  ls-dir.c  ls.h  ls-ls.c  ls-vdir.c
~/source/coreutils-5.93/coreutils-5.93/src$ [color=blue]ls e*.c[/color]
echo.c  env.c  expand.c  expr.c
~/source/coreutils-5.93/coreutils-5.93/src$

```

---

### Post by jasonlfunk on 2007-06-23
Cool. Thanks.

---

