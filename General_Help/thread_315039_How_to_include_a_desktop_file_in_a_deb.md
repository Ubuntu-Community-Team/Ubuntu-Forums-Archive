---
title: "How to include a desktop file in a deb?"
date: 2006-12-08
forum: General Help
---

### Post by viciouslime on 2006-12-08
I'm trying to package some software as a deb, it is working just fine so far but I can't figure out how to get it to appear in the menu. I know I need a desktop file, which I have managed to create and also an icon, but I don't know what to do to get these files to be included when the deb is built.

Can anyone help? :-D

---

### Post by gborzi on 2006-12-08
Put the desktop file and the icon under the debian directory, than add an install file, like this one that comes from my glest package:
glest.install
> debian/glest.xpm usr/share/pixmaps
debian/glest.desktop usr/share/applications
you may also need to create the directories, using the dirs file, like this
> usr/share/pixmaps
usr/share/applications
finally the dh_install line must be uncommented in the rules file.

---

### Post by yopnono on 2006-12-08
If you would like to know how a deb is built, then extract a deb. Take a deb that yo know includes a menu entry.

---

### Post by viciouslime on 2006-12-09
Thank you gborzi! I tired your suggestion already yopnono, but the deb files don't contain that information, the install file is only used to build the deb, it isn't part of it.

---

