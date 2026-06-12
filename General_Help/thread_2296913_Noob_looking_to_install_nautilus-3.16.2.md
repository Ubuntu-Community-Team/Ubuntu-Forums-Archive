---
title: "Noob looking to install nautilus-3.16.2"
date: 2015-09-29
forum: General Help
---

### Post by BarryD9545 on 2015-09-29
I'm trying to get the latest version of nautilus on my system, 15.04 Gnome, but I don't know what to do with the folder I've downloaded (nautilus-3.16.2.tar.xz).

I need to make and compile? I'm parroting here, I need to know the methods.

Thanks!

---

### Post by TheFu on 2015-09-30
It is a bad idea to install software outside the package management system.  That means either use the official repos or use a reputable PPA  that is actively maintained.  Why?  Security updates.

Whenever we decide to install outside the package management system, we've accepted to manually maintain all the software and all the dependencies for that software going forward.  For me, the **package management is the primary reason I prefer Linux distros over other OSes.**

Manually downloading and sort of file/package breaks the package management aspects for those files and may lock certain packages inside the system to the current level, even if there are security updates.  That is too large a risk for me.

If I haven't successfully talked you out of it ... 

[https://askubuntu.com/questions/92328/how-do-i-uncompress-a-tarball-that-uses-xz](https://askubuntu.com/questions/92328/how-do-i-uncompress-a-tarball-that-uses-xz) explains how to gain access to the files inside the compressed tar file.  Inside the resulting directories, there should be a README and INSTALL file. Read those and follow the instructions.  I suspect you'll need lots of other files - gnome dependencies, gnome development packages, etc... but it may be really easy. I dunno.

---

