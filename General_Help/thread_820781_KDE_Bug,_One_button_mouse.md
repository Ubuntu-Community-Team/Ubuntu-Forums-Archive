---
title: "KDE Bug, One button mouse"
date: 2008-06-06
forum: General Help
---

### Post by XPM on 2008-06-06
Using Kubuntu 8.04 remix with a standard USB mouse that has never given me any problems in the past.

However, after wine crashed and it crashed kdewin and everything along with it (no I didn't run it as root) I had to restart X and then back after I logged back in my right mouse button stopped working (I got 3 and that's including the mousewheel)

It just does not respond and I find this pretty weird..
I even tried to reboot the machine but for no good :(

Any ideas on how to reconfigure a mouse?

---

### Post by XPM on 2008-06-06
I believe this should be easy for those that know how...
Think it's a shame that it only gets one look because it's kde related

---

### Post by XPM on 2008-06-06
Now, I rewrote xorg.conf but to no help

This is my xorg.conf

-

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by TWO on 2008-06-06
> **XPM said:**
> I believe this should be easy for those that know how...
Think it's a shame that it only gets one look because it's kde related

I think it is more the fact that it is an unusual problem than the fact that it is KDE related...

Anyway, have you tried any other mice with your system? 

Also, any chance to try the mouse with another OS? (Do you dual boot?)

Would help to determine whether it's just a problem with Kubuntu or the mouse itself. 

KDE has extensive settings options so I reckon you should play around with them and see if you get any results.

---

