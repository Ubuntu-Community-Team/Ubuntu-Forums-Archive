---
title: "Add/Remove no longer works"
date: 2007-05-29
forum: General Help
---

### Post by citaworvk on 2007-05-29
Whenever I use click Applications>>Add/remove I get an hourglass then nothing happens. What is the command to run Add/Remove from terminal and what could possibly be mmy problem.

Thanks in advance.

---

### Post by deeZee on 2007-05-30
Hmmm...that's very strange.  I don't know what the command for "Add/Remove..." is, but you can launch the synaptic package manager by typing in the following: ```
gksudo synaptic
```

---

### Post by DoktorSeven on 2007-05-30
It's **gnome-app-install**

Run it from terminal and check the output.

---

### Post by citaworvk on 2007-05-31
This is the output I get:

Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 312, in <module>
    from AppInstall.AppInstall import AppInstall
  File "/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py", line 61, in <module>
    import dbus.glib
  File "/var/lib/python-support/python2.5/dbus/glib.py", line 33, in <module>
    from dbus.mainloop.glib import DBusGMainLoop, threads_init
  File "/var/lib/python-support/python2.5/dbus/mainloop/glib.py", line 25, in <module>
    from _dbus_glib_bindings import DBusGMainLoop, gthreads_init
ImportError: No module named _dbus_glib_bindings

By the way Synaptic works fine.

---

### Post by citaworvk on 2007-05-31
I used Synaptic to reinstall gnome app install, but I still get the same output when I try to start Add/Remove. 


My automatic update function doesn't work correctly either, I can install updates, but I can't see the updates before I activate them. 

Any help would be appreciated, thanks in advance.

---

### Post by citaworvk on 2007-06-04
The automatic update doesn't work properly either

---

### Post by DMM8787 on 2007-06-04
Same problem, heres my output from gnome-app-install:

Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 312, in <module>
    from AppInstall.AppInstall import AppInstall
  File "/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py", line 30, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk

---

### Post by citaworvk on 2007-06-05
I think the problem started after one of the updates. Any input would be helpful.

---

### Post by DMM8787 on 2007-06-05
All of these produce the same error as mine descibed above:

gnome-app-install
gnome-btdownload
gnome-codec-install
gnome-language-selector
gnome-schedule
gnome-sudoku

citaworvk: Do these programs launch for you? There must be some similarity in these which will help us solve the problem...

---

