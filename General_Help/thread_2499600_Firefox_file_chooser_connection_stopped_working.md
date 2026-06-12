---
title: "Firefox file chooser connection stopped working"
date: 2024-08-02
forum: General Help
---

### Post by fergus2 on 2024-08-02
Using Ubuntu 24.04 LTS,  Firefox is no longer opening file dialogs.

I can't save, download or open any files, basically. I've just switched to Firefox 130.0a1 (2024-07-30) (64-bit) in case it helps, but no (I think I was probably on 128.0.31- before).
It says things like this:

[Parent 14903, Main Thread] WARNING: Can't open portal file chooser: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface “org.freedesktop.portal.FileChooser” on object at path /org/freedesktop/portal/desktop: 'glib warning', file /build/firefox/parts/firefox/build/toolkit/xre/nsSigHandlers.cpp:187

(firefox-nightly:14903): Gtk-WARNING **: 18:56:58.540: Can't open portal file chooser: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface “org.freedesktop.portal.FileChooser” on object at path /org/freedesktop/portal/desktop

For what it's worth, Chromium is still working okay. I've tried reinstalling xdg-desktop-portal and xdg-desktop-portal-gtk and edubuntu-desktop, but it didn't seem to make any difference

Anyone got any ideas for what to try next?

Thanks!

---

### Post by currentshaft on 2024-08-02
.

---

