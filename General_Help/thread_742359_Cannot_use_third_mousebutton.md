---
title: "Cannot use third mousebutton"
date: 2008-04-01
forum: General Help
---

### Post by bigblop on 2008-04-01
I use Ubuntu 7.10.

When I select some text in either openOffice, gedit or geany with the mouse and try to paste it with the third mouse button nothing happens. It works fine in both Firefox and thunderbird.

This is the content of /etc/X11/xorg.conf:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection 

I have also tried to change:

        Option          "Emulate3Buttons"       "true"

to 

        Option          "Emulate3Buttons"       "false"

but that does not help (have made sure to reboot the system). Does anyone have an idea whats wrong with my system?

---

