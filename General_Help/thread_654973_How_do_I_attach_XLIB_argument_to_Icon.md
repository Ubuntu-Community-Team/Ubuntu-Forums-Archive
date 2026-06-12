---
title: "How do I attach XLIB argument to Icon?"
date: 2007-12-31
forum: General Help
---

### Post by kweejibo on 2007-12-31
I really like XnView and I've installed the newest version on my 7.10 setup. Alas, when I open an image with XnView, it shows up sort of ghostly transparent.

Did a little research and found this:

try starting your app with:
```
XLIB_SKIP_ARGB_VISUALS="1" appname
```

It works fine when I run XnView from the terminal. How do I go about attaching this to the icon so I can simply point and click in Gnome?

Thanks,
Josh

---

### Post by -grubby on 2007-12-31
create a .desktop icon and edit it with a text editor. Put the following lines in:

Name=Xlib
Exec=XLIB_SKIP_ARGB_VISUALS="1" xnview
Terminal=false
Icon= path/to/icon (they're usually in /usr/share/pixmaps)

---

### Post by kweejibo on 2008-01-07
Thanks, Nathangrubb. 

Here's what I did:

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Xlib
TryExec=xnview
Exec=XLIB_SKIP_ARGB_VISUALS="1" xnview
Icon=xnview.png
Terminal=false
Type=Application
Categories=GNOME;Application;Graphics;VectorGraphics;Viewer;X-Red-Hat-Base
GenericName[en_US]=

And here is the result:

There was an error launching the application.

Details: Failed to execute child process "XLIB_SKIP_ARGB_VISUALS=1" (No such file or directory)

---

