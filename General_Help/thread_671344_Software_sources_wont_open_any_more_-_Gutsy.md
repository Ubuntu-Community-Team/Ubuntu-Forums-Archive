---
title: "Software sources wont open any more - Gutsy"
date: 2008-01-18
forum: General Help
---

### Post by sipickles on 2008-01-18
Hi

I have been using gutsy without too many problems but now I have one.

If I go to System>Admin>Software sources, nothing happens.

'sudo synaptic' works in the terminal, as does 'sudo gedit /etc/apt/sources.list'

I'm getting the 'updates available' notification in the top bar, but I can't see what they are! I can choose to install all, but I don't always wanna do that :)

Thanks for any suggestions

Si

---

### Post by Christmas on 2008-01-18
It's probably a bug? I don't know but however until you find a solution you can try to update your system with 'sudo apt-get update && sudo apt-get upgrade'. Type it in a GNOME Terminal.

---

### Post by ugm6hr on 2008-01-18
This is the command to launch it from Terminal:
```
gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk

```

That might at least explain why it isn't starting.

---

### Post by sipickles on 2008-01-18
Indeed it does produce a lovely python traceback:

```
simon@simon-desktop:~$ gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
  File "/usr/bin/software-properties-gtk", line 27, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 38, in <module>
    import gobject as _gobject
  File "/var/lib/python-support/python2.5/gtk-2.0/gobject/__init__.py", line 30, in <module>
    from gobject.constants import *
  File "/var/lib/python-support/python2.5/gtk-2.0/gobject/constants.py", line 22, in <module>
    from _gobject import type_from_name
ImportError: /var/lib/python-support/python2.5/gtk-2.0/gobject/_gobject.so: undefined symbol: PyUnicodeUCS4_FromObject

```

Does that help?

---

### Post by ruiying on 2008-03-04
./configure --enable-unicode=ucs4
make
make install

---

