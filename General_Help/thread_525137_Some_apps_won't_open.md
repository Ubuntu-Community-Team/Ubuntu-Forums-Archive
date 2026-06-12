---
title: "Some apps won't open"
date: 2007-08-14
forum: General Help
---

### Post by jbrown101st on 2007-08-14
The problem is that when I try to open various programs (so far they seem to be "default" apps such as add/remove and alacarte) it just shows a message in the task bar saying "starting alacarte" and disappears after about 15 seconds.

   Another problem that just started happening along side this is when i hit ctrl+f or a couple other ctrl combos, FF closes.

  I ran alacarte in the terminal and got this error:

```
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 20, in ?
    from Alacarte.GnomeFront import GnomeFront
  File "/usr/lib/python2.4/site-packages/Alacarte/GnomeFront.py", line 22, in ?
    import gtk, gtk.glade, gnome, gnome.ui, gobject
  File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 45, in ?    from _gtk import *
ImportError: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: cairo_pdf_surface_create

```

Oh, and I'm using Dapper Drake 6.06

Any help would be appreciated...

---

