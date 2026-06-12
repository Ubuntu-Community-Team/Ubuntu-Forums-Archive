---
title: "Keyboard custom udev rule"
date: 2013-04-03
forum: General Help
---

### Post by belnac on 2013-04-03
I use a keyboard switch so as to use the same keyboard on two machines. Unfortunately using the kb switch results in the keyboard rate being lost and so I thought of creating a custom udev rule to restore it.

Firstly I looked in the kernel log for the device in question. Then issued `[FONT=Courier New]udevadm info --query=property --path=/devices/pci0000:00/0000:00:1d.1/usb8/8-1/8-1:1.1/input/input16[/FONT]' [0]

After trying all sorts of different properties I settled for a very simple udev rule:

[FONT=Courier New]ACTION="add", ENV{ID_MODEL}=="USB_Keyboard", RUN+="/usr/bin/xset r rate 200 30"[/FONT]

Also tried setting the udev rule to run a script but no joy.

Anyone has any idea how I can get this to work?



[0] [http://paste.ubuntu.com/5657723/](http://paste.ubuntu.com/5657723/)

---

