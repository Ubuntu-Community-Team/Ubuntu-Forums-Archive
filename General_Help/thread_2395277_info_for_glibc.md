---
title: "info for glibc"
date: 2018-06-29
forum: General Help
---

### Post by sundaresh on 2018-06-29
I would like to install glibc particularly info for glibc as well, ideally the latest version, as also other c/c++ gnu development tools complete. How ?

---

### Post by steeldriver on 2018-06-29
Your system already depends intimately on glibc (as package libc6)

You can get the glibc development libraries and headers, C & C++ compilers, GNU make, plus a couple of other things by installing the build-essential metapackage:

```

$ apt-cache depends build-essential
build-essential
 |Depends: libc6-dev
  Depends: <libc-dev>
    libc6-dev
  Depends: gcc
  Depends: g++
  Depends: make
    make-guile
  Depends: dpkg-dev

```

This will install (via manpages-dev) the basic documentation such as the section 3 manpages for common C/C++ functions such as the printf family - if that's not what you are looking for, there is additional documentation packed in glibc-doc

---

### Post by sundaresh on 2018-06-30
```
apt-cache depends build-essential
``` generates the same output as you have shown. So I did apt-cache for each of the packages separately, and the concatenated output of each of them is
 
```
libc6-dev
  Depends: libc6
  Depends: libc-dev-bin
    libc-dev-bin:i386
  Depends: linux-libc-dev
  Conflicts: <libc0.1-dev>
  Conflicts: <libc0.3-dev>
  Conflicts: <libc6.1-dev>
  Breaks: binutils
  Breaks: <binutils-gold>
  Breaks: cmake
  Breaks: <gcc-4.4>
  Breaks: <gcc-4.5>
  Breaks: <gcc-4.6>
  Breaks: libhwloc-dev
  Breaks: libjna-java
  Breaks: liblouis-dev
  Breaks: liblouisxml-dev
  Breaks: make
  Breaks: pkg-config
  Suggests: glibc-doc
  Suggests: manpages-dev
gcc
  Depends: cpp
  Depends: gcc-5
  Conflicts: gcc-doc
 |Recommends: libc6-dev
  Recommends: <libc-dev>
    libc6-dev
  Suggests: gcc-multilib
  Suggests: make
    make-guile
  Suggests: manpages-dev
  Suggests: autoconf
  Suggests: automake
  Suggests: libtool
  Suggests: flex
  Suggests: bison
    bison:i386
  Suggests: gdb
  Suggests: gcc-doc
g++
  Depends: cpp
  Depends: gcc
  Depends: g++-5
  Depends: gcc-5
  Suggests: g++-multilib
make
  Depends: libc6
  Conflicts: make-guile
  Suggests: make-doc
  Replaces: make-guile
make-guile
  Depends: guile-2.0-libs
  Depends: libc6
  Conflicts: make
  Suggests: make-doc
  Replaces: make
    make-guile
dpkg-dev
  Depends: libdpkg-perl
  Depends: bzip2
    bzip2:i386
  Depends: xz-utils
    xz-utils:i386
  Depends: patch
    patch:i386
  Depends: make
    make-guile
  Depends: binutils
  Depends: base-files
    base-files:i386
  Breaks: devscripts
  Breaks: dpkg-cross
 |Recommends: gcc
  Recommends: <c-compiler>
    bcc
    clang-3.5
    clang-3.6
    clang-3.7
    clang-3.8
    clang-3.9
    clang-4.0
    clang-5.0
    clang-6.0
    gcc
    gcc-4.7
    gcc-4.8
    gcc-4.9
    gcc-5
    tcc
  Recommends: build-essential
  Recommends: fakeroot
    fakeroot:i386
    pseudo:i386
    pseudo
 |Recommends: gnupg
    gnupg:i386
  Recommends: gnupg2
    gnupg2:i386
 |Recommends: gpgv
    gpgv:i386
  Recommends: gpgv2
    gpgv2:i386
  Recommends: libalgorithm-merge-perl
  Suggests: debian-keyring
  Replaces: manpages-it

```
I wanted to attach this output as a file but could not, said invalid file. libc6-dev is installed. But no info on gnu tools glibc or gcc or make ..... . So apt install gcc-doc installed info for gcc,g++ 5. As you have mentioned should I install gibc-doc package for the info on glibc. make utility is already present. I just need info on that.

---

### Post by steeldriver on 2018-06-30
What actual problem are you trying to solve? is there some particular program that's not working, or documentation that you believe to be missing?

---

### Post by sundaresh on 2018-07-01
Just the info that is all. Most of the tools I know and can handle are already available, even if they are a bit older versions, that is ok. Just the info for those. I have installed glibc-doc. In like manner I would like to install info for make, and gdb  , maybe ranlib and ar.

---

### Post by Impavidus on 2018-07-01
Most documentation is in packages with the same name as the main package for that software, with the suffix -doc. So try installing make-doc, gdb-doc. Also try the synaptic package manager and browse packages in the Documentation category.

---

### Post by steeldriver on 2018-07-01
I'm not sure if you are using "info" generically or are referring to the node files for the GNU info documentation specifically

If the latter, then as Impavidus has noted, those for make and gdb are provided by make-doc and gdb-doc respectively

The ar and ranlib commands are both part of GNU binutils and their info nodes are provided by binutils-doc

Personally I don't think I've ever needed to install these packages manually - they always seem to be installed as suggested or recommended by the package manager

---

### Post by sundaresh on 2018-07-01
Just what I needed to know. Much thanks to all of you.

---

