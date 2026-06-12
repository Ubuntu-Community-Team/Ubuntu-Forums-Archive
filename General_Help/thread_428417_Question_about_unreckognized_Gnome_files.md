---
title: "Question about unreckognized Gnome files"
date: 2007-04-30
forum: General Help
---

### Post by rillip on 2007-04-30
I'm running KDE, don't have Gnome installed.  I think the only Gnome app I have installed is gparted.

I found the following files in /home/myuser while looking for something else. Are these needed or can I remove them?  I have the space so it's not really too much of an issue, I'm just not aware of why I would have them.

gconf
.gconfd
.gnome
.gnome2
.gnome2_private
.gnupg
.gphoto
.gstreamer-0.10
.gtk-bookmarks
.gtk_qt_engine_rc


Thanks for any info you can provide

---

### Post by mexlinux on 2007-05-01
gconf is something similar to the windows registry for gnome.
Therefor some programs use it to store preferences, for instantce you refere to gtk-qt-engine wich is what makes the gtk apps use qt to be drawn in kde, etc,
That folder contains just prefereces, that some program will use

---

