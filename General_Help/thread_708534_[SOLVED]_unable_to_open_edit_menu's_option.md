---
title: "[SOLVED] unable to open edit menu's option"
date: 2008-02-26
forum: General Help
---

### Post by terry_gardener on 2008-02-26
I am unable to open the edit menu option (right click application and click edit menu) it says starting edit menu in the taskbar/panel and the it disappears and nothing happens. 

I have also rebooted x server (ctrl-alt-backspace), also rebooted system, also tried reinstall of python 2.5 min and alacarte. 

when i run alacarte from the terminal i get an error. 

Traceback (most recent call last):
  File "/usr/bin/alacarte", line 22, in <module>
    from Alacarte.MainWindow import MainWindow
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 19, in <module>
    import gtk, gtk.glade, gmenu, gobject, gnomevfs, gnome.ui
  File "/var/lib/python-support/python2.5/gtk-2.0/gnome/__init__.py", line 13, in <module>
    from _gnome import *
ImportError: /usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf

can someone please HELP.

---

### Post by terry_gardener on 2008-02-26
solved 

i tried reinstalling alacarte again i also reinstalled the ubuntu desktop and still got the same problem. 

I then reinstalled the python 2.5 package and it now works. 

i only tried the python 2.5 minimum package last time.

---

