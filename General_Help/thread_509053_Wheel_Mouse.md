---
title: "Wheel Mouse"
date: 2007-07-25
forum: General Help
---

### Post by cbhargava on 2007-07-25
Hi,

First of all I would like to apologize if this has already been covered. Before posting, I had looked for this issue at various places including ubuntu forums.  :(

I have a logitech M-BT96a mouse. It is both PS2 as well as a USB mouse and works with the green adapter.

If I use this mouse on a USB port he wheel works in a perfect order but if I use the mouse on a PS/2 port the wheel doesn't work.  ](*,)

I have tried tweaking xorg.conf on my feisty desktop. Here is the current mouse section in my xorg.conf

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        #Option         "Device"                "/dev/input/mice"
        Option          "Device"                "/dev/psaux"
        #Option         "Protocol"              "ExplorerPS/2"
        Option          "Protocol"              "auto"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
        Option          "EmulateWheel"          "true"
EndSection

Would appreciate some pointers. :(

---

### Post by cbhargava on 2007-07-27
Thank You Experts!

---

