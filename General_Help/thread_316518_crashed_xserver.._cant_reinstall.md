---
title: "crashed xserver.. cant reinstall"
date: 2006-12-10
forum: General Help
---

### Post by g3k0 on 2006-12-10
Hey, I managed to crash xserver.  I tried removing but since I am behind a http proxy I cant download anything without logging in.  I need GUI to log in.  So i put an xserver installer on a cd.  It reads the cd in command line but when i enter cdrom0 nothiing is in there.  Any ideas?????

---

### Post by tzulberti on 2006-12-11
You could reconfigure xserver from a console doing: sudo dpkg-reconfigure xserver-xorg

The cd isn't mount automatically because of that gnome take cares. Nevertheless, you should be able to mount it using: mount /media/cdrom

---

