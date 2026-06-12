---
title: "GTK Trouble"
date: 2008-04-27
forum: General Help
---

### Post by _kAz_ on 2008-04-27
Hi!!! I'm Lucas from Argentina...

I'll describe my problem. It happens when I try to open Emesene or Wine-Doors. This is what I get from the Konsole:

[I][INDENT]Traceback (most recent call last):
File "/usr/share/emesene/emesene_launcher", line 31, in ?
import Controller
File "/usr/share/emesene/Controller.py", line 21, in ?
import gtk
ImportError: No module named gtk[/INDENT][/I]

I've tried to install (or re-install) gtk-libraries with *sudo aptitude install python-gtk2*, but this command just uninstalled some libraries and the problem is still there.

What can I do?

---

