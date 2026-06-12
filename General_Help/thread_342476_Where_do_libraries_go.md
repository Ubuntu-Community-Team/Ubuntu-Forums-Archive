---
title: "Where do libraries go?"
date: 2007-01-20
forum: General Help
---

### Post by underwater on 2007-01-20
I was just wondering where you normally put libraries that are needed by other programs that you are trying to build? 

I ask because I'm trying to build the ktigcc program from source and it needs libticonv.  Since this isn't in the repos, I've downloaded and unpacked the tar.bz file.  However, I still have no idea where it should go so that qmake, which is called by ./configure, knows how to find it.

I'm assuming that qmake is looking in the standard place for it, which it isn't there yet.  What is this standard place for libraries and can I just move the libticonv folder into that dir?


Thanks in advance,
underwater

---

### Post by zanglang on 2007-01-20
it's usually /usr/lib, or /usr/local/lib if you'd like to separate the library from system default ones. If your library package has a Makefile try doing "sudo make install" and it should copy them to the appropriate directories.

---

