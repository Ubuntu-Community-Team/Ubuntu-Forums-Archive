---
title: "ubuntu 22.10 settings not starting"
date: 2023-01-22
forum: General Help
---

### Post by strange on 2023-01-22
when i run it from commandline i get this:

strange@echelon:~$ gnome-control-center 

(gnome-control-center:14464): GLib-GObject-WARNING **: 12:15:46.568: invalid cast from 'GdkWaylandToplevel' to 'GdkX11Surface'

(gnome-control-center:14464): GLib-GObject-WARNING **: 12:15:46.568: invalid cast from 'GdkWaylandDisplay' to 'GdkX11Display'
Segmentation fault (core dumped)
strange@echelon:~$

---

### Post by hidekiai2 on 2023-07-09
> **strange said:**
> when i run it from commandline i get this:

strange@echelon:~$ gnome-control-center 

(gnome-control-center:14464): GLib-GObject-WARNING **: 12:15:46.568: invalid cast from 'GdkWaylandToplevel' to 'GdkX11Surface'

(gnome-control-center:14464): GLib-GObject-WARNING **: 12:15:46.568: invalid cast from 'GdkWaylandDisplay' to 'GdkX11Display'
Segmentation fault (core dumped)
strange@echelon:~$

For prosperities, in case others have encountered this...

Please note that I do not use Ubuntu, but the above happens on latest Debian (debian 12 bookworm) with Gtk4.  From what I understand, it's something to do with 'xwayland', and the solution (from command line) is:

```

$ GDK_BACKEND=x11 gnome-control-center

```

---

