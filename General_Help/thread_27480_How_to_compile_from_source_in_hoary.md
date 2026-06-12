---
title: "How to compile from source in hoary?"
date: 2005-04-16
forum: General Help
---

### Post by bk452 on 2005-04-16
I would like to install 2 apps from gnomefiles but they are in source code.  Can someone point me to directions on compiling from source that a mother can understand?

---

### Post by p!=f on 2005-04-16
[QUOTE=bk452]I would like to install 2 apps from gnomefiles but they are in source code.  Can someone point me to directions on compiling from source that a mother can understand?[/QUOTE]
This is a must read:
[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)
Quick guide:
* Unpack the sources, ie. ~/src/gnome-art-0.1/
* cd ~/src/gnome-art-0.1/
* dh_make (you will select 'single' mostly) to "debianize" the sources
* dpkg-buildpackage -rfakeroot
or
* fakeroot debian/rules binary

---

### Post by bk452 on 2005-04-16
Thanks!!!  I have one app installed and it works great.  I'll work on the other.

---

