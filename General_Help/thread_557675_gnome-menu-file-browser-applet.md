---
title: "gnome-menu-file-browser-applet"
date: 2007-09-22
forum: General Help
---

### Post by mmize on 2007-09-22
Has anyone tried installing the gnome-menu-file-browser-applet?  When I execute make I get the following output.

/home/mmize/menu-file-browser-applet-0.5.1/src/main.c:26:21: error: gtk/gtk.h: No such file or directory
/home/mmize/menu-file-browser-applet-0.5.1/src/main.c:27:26: error: panel-applet.h: No such file or directory
In file included from /home/mmize/menu-file-browser-applet-0.5.1/src/main.c:28:
/home/mmize/menu-file-browser-applet-0.5.1/src/menu-browser.h:29:26: error: glib/gprintf.h: No such file or directory
/home/mmize/menu-file-browser-applet-0.5.1/src/menu-browser.h:31:35: error: libgnomeui/libgnomeui.h: No such file or directory
/home/mmize/menu-file-browser-applet-0.5.1/src/menu-browser.h:32:35: error: libgnomevfs/gnome-vfs.h: No such file or directory
/home/mmize/menu-file-browser-applet-0.5.1/src/menu-browser.h:33:49: error: libgnomevfs/gnome-vfs-mime-handlers.h: No such file or directory
In file included from /home/mmize/menu-file-browser-applet-0.5.1/src/menu-browser.h:35,

The projects homepage (listed below) says you need gtk2.  I installed libgtk20-dev but didn't have any luck.  Any help would be appreciated.

[http://code.google.com/p/gnome-menu-file-browser-applet/](http://code.google.com/p/gnome-menu-file-browser-applet/)

---

### Post by mmize on 2007-09-23
Fixed :p

---

