---
title: "Mouse Goes Haywire"
date: 2008-05-17
forum: General Help
---

### Post by wburglett on 2008-05-17
I recently upgraded to Hardy Heron and the first thing I noticed about the new version (after the loading bar) was that my mouse didn't work at all. I even tried plugging in a generic mouse in hopes that it would be recognized, it wasn't. Thankfully by editing the xconfig, I was able to get the mouse to work again. However, since then, whenever I load a full screen or wine application, my mouse goes completely out of control, bouncing off the walls of the window regardless of what I attempt to do.

I am using a Logitech Mx-Laser wireless mouse (connected through usb). The lines of my xorg.conf file of interest are:

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "evdev"
    Option         "Name" "Logitech USB Receiver"
    Option         "Device" "/dev/input/event1"
    Option         "CorePointer"
    Option         "Protocol" "auto"
    Option         "ZAxisMapping" "4 5"
EndSection

Thank you!

---

