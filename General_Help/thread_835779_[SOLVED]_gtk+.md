---
title: "[SOLVED] gtk+"
date: 2008-06-20
forum: General Help
---

### Post by theshadowwithanmp5n on 2008-06-20
i have been trying to compile wxPython from source and i keep getting this message when i run ./configure



configure: error:
The development files for GTK+ were not found. For GTK+ 2, please
ensure that pkg-config is in the path and that gtk+-2.0.pc is
installed. For GTK+ 1.2 please check that gtk-config is in the path,
and that the version is 1.2.3 or above. Also check that the
libraries returned by 'pkg-config gtk+-2.0 --libs' or 'gtk-config
--libs' are in the LD_LIBRARY_PATH or equivalent.

can anyone tell me how to fix this error?:confused:

---

### Post by Steveway on 2008-06-20
Wxpython is in the repositories, you can install it with Synaptic.
No need to compile anything.

---

### Post by Nameless_one on 2008-06-20
However, for future reference:

1) GTK+ is the library Gnome is built on. 
2) When compiling something from source, it might depend on some programming libraries, which you should install. If you know what they are, you can install them through synaptic, although bear in mind that you need the -dev versions, not the regular ones. 

This particular error tells you that you need the GTK+ library (the development files, ie the -dev). This package is probably the one you're looking for: libgtk2.0-dev 

However, installing the version of wxPython from the repositories is the quickest and most convenient solution. You would only need to compile from source if for some reason you need to install a newer version than the one in the repo (as they aren't always the latest).

---

