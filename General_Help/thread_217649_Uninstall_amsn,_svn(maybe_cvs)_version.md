---
title: "Uninstall amsn, svn(maybe cvs) version?"
date: 2006-07-17
forum: General Help
---

### Post by Poka64 on 2006-07-17
Maybe not the right place to ask, but how do I uninstall the cvs(svn?) version of amsn, i did the whole "make install" procedure, but I can't "make uninstall" :/

Got a folder with: branches tags trunk

The thing is, I somehow managed to install it (and it works), but I can't uninstall it now :(

---

### Post by givré on 2006-07-17
Unfortynatly, there is no uninstall in the Makefile. But there is support for deb & rpm. If you do make deb, you will have a .deb in distrub/DEB, and install it + uninstall it will have the same effect has what you want to do.

---

