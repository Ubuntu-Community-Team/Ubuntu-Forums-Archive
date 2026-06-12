---
title: "kubuntu user needs additional programme"
date: 2016-07-03
forum: General Help
---

### Post by anon_private on 2016-07-03
[INDENT]                             I have installed the Stylus Toolbox that offers a GUI for esputil. I obtained the utility form Source Forge.

I cannot find the program in my start menu (Homerun Kicker), and when I type stylus-toolbox in Konsole I see

andrew@andrew-Dell-DM061:~$ stylus-toolbox
Traceback (most recent call last):
  File "/usr/bin/stylus-toolbox", line 34, in <module>
    from GladeWindow import *
  File "/usr/share/stylus-toolbox/GladeWindow.py", line 11, in <module>
    import gtk.glade
ImportError: No module named glade

A crash report is given in System Notification

I see a number of programs in the kubuntu repository that indicate Glade. Which one do I need to install?

Help please.

PS. Printer is Epson Stylus SX100                        
[/INDENT]

---

### Post by anon_private on 2016-07-03
Further information: installed : python-glade2: Now

I typed stylus-toolbox in konsole and the ink level diagrams appeared.  However, they are set to zero. This is wrong, I can print. I was pleased  to see that my printer is listed in the supported printers list;  however, I don't think that the changes are being saved in .stylus-toolbox.conf because the command prompt did not return when I  saved the preference.

Couple of other points. I can't find stylus-toolbox in the menu system.  Do you know where it might be located. There should be an icon in the  tray, this is also missing.

Overall, progress being made.

Best wishes.

Ps. I have just looked at .stylus-toolbox.conf in my home directory. It looks like SX100 (my printer) is saved

device]
raw device = 
is newer usb printer = True
model = escp2-sx100

[external programs]
escputil binary = /usr/bin/escputil

When i type escputil --ink-level

I see

'andrew@andrew-Dell-DM061:~$ escputil --ink-level
Escputil version 5.2.10-pre2, Copyright (C) 2000-2006 Robert Krawitz
Escputil comes with ABSOLUTELY NO WARRANTY; for details type 'escputil -l'
This is free software, and you are welcome to redistribute it
under certain conditions; type 'escputil -l' for details.

Obtaining ink levels requires using a raw device.'

I have more success when running stylus-toolbox, although the ink levels are not being recorded.

I may need to locate the Device Port.

The only information that I can glean from the CUPS interface is:
usb://EPSON/Stylus%20SX100?serial=KQEZ387420&interface=1

This is not a hard disk path. I have never been able to locate this path - from the hard dive to the printer

---

