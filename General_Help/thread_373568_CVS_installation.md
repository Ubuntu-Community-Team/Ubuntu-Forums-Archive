---
title: "CVS installation"
date: 2007-03-01
forum: General Help
---

### Post by alexfoullon on 2007-03-01
Hi everybody,

This is my first post , and thanks for the forums I was solving many things. But now I come across something that I couldn't find. My problem is that I want to install autopano-sift and the panotools  in my pc. I downloaded the latest via cvs, but to make it work I am aware that you need the packages libtool, autoconf and automake1.7. I am trying to install the software with the following commands:

$ cd libpano/
$ ./bootstrap
$ ./configure
$ make
$ sudo make install

When I try ./bootstrap it says "You must have autoconf installed to compile libpano."

I checked that with:
$ sudo apt-get install autoconf
...and there is no problem, it is already in the newest version. I also checked it in the SPM

Any hint will be useful

Thanks in advance

---

