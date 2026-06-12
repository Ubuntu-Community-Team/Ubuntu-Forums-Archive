---
title: "symbol lookup error: undefined symbol: _gfortran_internal_malloc64"
date: 2013-05-08
forum: General Help
---

### Post by FotiX on 2013-05-08
Ubuntu 13.04 here.

I was trying to use a program called smartpca and the first time I tried to use it, it raised a dependency error about a liblapack.

I installed libatlas3-base and it was solved. Then it raised another error about libgfortran.so.1. Since I had all libfortran packages installed, i created a link between libgfortran.so.3 and libgfortran.so.1.

Then I ran the program again and it raised that error:

./smartpca: symbol lookup error: ./smartpca: undefined symbol: _gfortran_internal_malloc64

From what I read, I understand that on Fedora you have to install gfortran 4.1.

How can I solve this?

---

### Post by FotiX on 2013-05-10
Ok solved it, I needed to remake the program from the source:

> This is one way that eigensoft has been installed
on a Ubuntu computer.

First install the dependencies:
gfortran
liblapack-dev

Now cd to the src directory and build as follows:
$ make all
$ make install

At this point you should have some files in the eigensoft/bin directory.
Note that the installation does not require admin privileges
and does not put files anywhere outside of the eigensoft directory tree.

To uninstall, cd to the src directory and run:
$ make clobber

To check that eigensoft has reverted to the pre-installed state,
check git status if eigensoft has been cloned from a git repo.

---

