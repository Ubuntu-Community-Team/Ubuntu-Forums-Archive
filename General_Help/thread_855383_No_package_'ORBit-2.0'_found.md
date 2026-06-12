---
title: "No package 'ORBit-2.0' found"
date: 2008-07-10
forum: General Help
---

### Post by Mr.Jkate on 2008-07-10
I've download code for gnome-panel for ubuntu 7.1.

As per instructions I just executed ./configure script and I'm getting following errors. Any idea how to fix this ?
========================================================================
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PANEL... configure: error: Package requirements (ORBit-2.0 >= 2.4.0 gdk-pixbuf-2.0 >= 2.7.1 pango >= 1.15.4 gtk+-2.0 >= 2.11.3 glib-2.0 >= 2.13.0 libgnome-2.0 >= 2.13.0 libgnomeui-2.0 >= 2.5.4 libbonoboui-2.0 >= 2.1.1 gnome-desktop-2.0 >= 2.11.1 gnome-vfs-2.0 >= 2.14.2 libglade-2.0 >= 2.5.0 gconf-2.0 >= 2.6.1 libgnome-menu >= 2.11.1 dbus-glib-1 >= 0.60) were not met:

No package 'ORBit-2.0' found
No package 'gdk-pixbuf-2.0' found
No package 'pango' found
No package 'gtk+-2.0' found
No package 'glib-2.0' found
No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found
No package 'libbonoboui-2.0' found
No package 'gnome-desktop-2.0' found
No package 'gnome-vfs-2.0' found
No package 'libglade-2.0' found
No package 'gconf-2.0' found
No package 'libgnome-menu' found
No package 'dbus-glib-1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PANEL_CFLAGS
and PANEL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by jerome1232 on 2008-07-10
> No package 'ORBit-2.0' found
probably need to install that package, the following command shows that ubuntu has a package called orbit2, try to install it and report back
```
sudo apt-cache search orbit2
```

---

