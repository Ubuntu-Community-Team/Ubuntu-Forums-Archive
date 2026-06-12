---
title: "Problem compiling/installing MAME frontend (broken pipe?)"
date: 2008-05-18
forum: General Help
---

### Post by painaxl on 2008-05-18
I've been trying to compile and install [Gnome Video Arcade]("https://sourceforge.net/projects/gva/"), a frontend for MAME.  I've finally gotten all of the required dev packages (I think), but when I do checkinstall, I get this in the log:

> 
Unpacking gnome-video-arcade (from .../gnome-video-arcade_0.6.1-1_i386.deb) ...
dpkg: error processing /usr/local/src/gnome-video-arcade-0.6.1/gnome-video-arcade_0.6.1-1_i386.deb (--install):
 trying to overwrite `/var/lib/scrollkeeper/scrollkeeper_docs', which is also in package gnome-lirc-properties
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /usr/local/src/gnome-video-arcade-0.6.1/gnome-video-arcade_0.6.1-1_i386.deb


Any idea what this means?  I'm still trying to get the hang of compiling and installing packages from the source.  Thanks!

---

