---
title: "How to force reinstall a package to recover deleted files?"
date: 2007-04-28
forum: General Help
---

### Post by CaptSaltyJack on 2007-04-28
I goofed up.. I accidentally trashed a couple important files in the "cpp-4.1" package.  How do I make it so apt-get will download the package and put back any files that are missing?  Surely there must be a way to do this..

---

### Post by taurus on 2007-04-29
Try something like

```
sudo aptitude update
sudo aptitude install build-essential
```
cpp is part of the build-essential package.

---

### Post by CaptSaltyJack on 2007-04-29
Nope.  /usr/lib/gcc/i486-linux-gnu/4.1.2/cc1 is still missing.

If I could somehow download the cpp-4.1.deb package, I bet "dpkg -i" would fix it.

EDIT: Got it.  apt-get --reinstall install cpp-4.1

---

### Post by taurus on 2007-04-29
[http://packages.ubuntu.com/edgy/interpreters/cpp-4.1](http://packages.ubuntu.com/edgy/interpreters/cpp-4.1)

or

[http://packages.ubuntu.com/edgy/allpackages](http://packages.ubuntu.com/edgy/allpackages)

---

