---
title: "How to tar the current directory without making a tar-bomb?"
date: 2007-12-17
forum: General Help
---

### Post by kinghajj on 2007-12-17
I'm writing a Makefile and I want it to be able to create a tar.bz2 archive of the current directory. However, if you execute "tar xjf archive.tar.bz2 *", the resulting archive is a tar-bomb. Is there a way to create a non-tar bomb archive of the current directory?

---

### Post by dagnabit dang doohickey on 2007-12-17
```
tar xj -C ../ -f ../archive.tar.bz2 currentdir
```

It becomes a little more obvious if written like this:
```
tar xj -f ../archive.tar.bz2 -C ../ currentdir
```
But, its also easy to overlook the space between the source directory and the change directory option.

---

