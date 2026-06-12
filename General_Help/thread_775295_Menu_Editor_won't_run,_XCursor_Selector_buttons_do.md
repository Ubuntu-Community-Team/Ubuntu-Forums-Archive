---
title: "Menu Editor won't run, XCursor Selector buttons do nothing"
date: 2008-04-30
forum: General Help
---

### Post by Quatrix on 2008-04-30
1. After using Ubuntu 8.04 for a couple of days, the Menu Editor (alacarte) stopped working (it had been okay before), whether I run it from the menu, "Edit Menus" in the right-click context menu, or directly via the Run dialog.  I used apt-get to remove it and install it again.  Same problem.

2. The "Install Theme" and "Go to Theme Folder" buttons in XCursor Selector (gcursor) never worked.  I click, and nothing happens.

Any ideas?

---

### Post by Quatrix on 2008-05-04
Okay, the gcursor thing also happens on another fresh install, so I assume it's a known issue.  But I'm still unable to run the menu editor, and it's becoming a pain.

---

### Post by Quatrix on 2008-06-04
Fixed!  I ran alacarte from the command line and saw the following.  I searched for the error message at the bottom and came across a solution (or at least a work-around) at [http://4front-tech.com/forum/viewtopic.php?t=2570&view=next&sid=706f3ffd9dd1cdf7d0a2800ad2b516f2](http://4front-tech.com/forum/viewtopic.php?t=2570&view=next&sid=706f3ffd9dd1cdf7d0a2800ad2b516f2).  I hope this helps someone else.

/usr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 22, in <module>
    from Alacarte.MainWindow import MainWindow
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 19, in <module>
    import gtk, gtk.glade, gmenu, gobject, gnomevfs, gnome.ui
  File "/var/lib/python-support/python2.5/gtk-2.0/gnome/__init__.py", line 13, in <module>
    from _gnome import *
ImportError: /usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf

---

