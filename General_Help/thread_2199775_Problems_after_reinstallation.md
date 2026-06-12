---
title: "Problems after reinstallation"
date: 2014-01-15
forum: General Help
---

### Post by ggodone on 2014-01-15
I recently reinstalled Ubuntu GNOME on my late 2012 Macbook Pro, and now I'm having two big issues.

1) I can't change my volume. Under Sound in System Settings the Output Volume bar is grayed out and there's no devices under the Input and Output tabs. There's no sound setting in the activity bar on the top and the multimedia keys (F10-F12) don't change the volume. However sound is still coming out, despite my inability to change the volume.

2) Steam displays this error window upon launch:
```
You are missing the following 32-bit libraries, and Steam may not run:
libXrandr.so.2
libpangoft2-1.0.so.0
libpango-1.0.so.0
libfreetype.so.6
libfontconfig.so.1
libgobject-2.0.so.0
libglib-2.0.so.0
libgio-2.0.so.0
libgtk-x11-2.0.so.0
libpulse.so.0
libgtk-x11-2.0.so.0
libgdk-x11-2.0.so.0
libpangocairo-1.0.so.0
libgdk_pixbuf-2.0.so.0
libcairo.so.2
libpango-1.0.so.0
libfreetype.so.6
libfontconfig.so.1
libgobject-2.0.so.0
libglib-2.0.so.0
libXi.so.6
libasound.so.2
libXrender.so.1
libdbus-1.so.3
libpng12.so.0
libgcrypt.so.11
libXcursor.so.1
libXinerama.so.1
libXi.so.6
libXrandr.so.2
libXss.so.1
libgssapi_krb5.so.2
libgnutls.so.26
libavahi-common.so.3
libavahi-client.so.3
```
However I've looked through some of these in Synaptic, and I've found that packages like libasound IS installed.

---

