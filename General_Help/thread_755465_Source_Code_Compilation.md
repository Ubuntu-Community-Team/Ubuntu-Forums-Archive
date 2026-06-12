---
title: "Source Code Compilation?"
date: 2008-04-14
forum: General Help
---

### Post by W.Sorting on 2008-04-14
Technically, with the source code of an upgraded program, is it possible to compile it and get a working version of a program that is not designed for that specific Ubuntu distribution?
(ex. running a Ubuntu 7.10 program on Ubuntu 7.04)

Thanks

---

### Post by rogirwin on 2008-04-14
What are you trying to run? Most third party applications can be installed regardless of what version of ubuntu the are deigned for.

if you have the source code you can try compiling the program yourself.

with something like:

tar zxvf files.tar.gz
cd path_to_files
./configure
make

You may be able to run it at this point.

if you wish to install it you can with "sudo make install"

But you are better doing this from a .deb package. It's possible that installing something from source may break your system or part of it depending on what it is.

Have a look here: [https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)

---

