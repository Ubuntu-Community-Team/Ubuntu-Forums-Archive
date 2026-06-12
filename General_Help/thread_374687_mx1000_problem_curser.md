---
title: "mx1000 problem curser"
date: 2007-03-02
forum: General Help
---

### Post by PoisoN2003 on 2007-03-02
Hey im using mx1000 when i use it works fine but sometimes for no reason mouse just moves up while im using it 
Its not a big problem but very annoying anyone know how to fix that>?
It does the same thing when i dont have the drivers for the mouse installed in windows

---

### Post by Cappy on 2007-03-03
$sudo nano /etc/X11/xorg.conf

You should see something like this:

Section "InputDevice"
 Identifier "MX1000"
 Driver     "mouse"
 Option     "CorePointer"
 Option     "Protocol"        "evdev"
 Option     "Dev Name"        "Logitech USB Receiver"
 Option     "Buttons"         "12"
 Option     "ZAxisMapping"    "11 12 10 9"
 Option     "Resolution"      "800"
 Option     "Emulate3Buttons" "false"
EndSection

change  - Option     "ZAxisMapping"    "11 12 10 9"
to -  Option     "ZAxisMapping"    "11 12"

That will fix it hopefully.

---

