---
title: "Microsoft Wireless Laser Mouse 5000"
date: 2007-12-20
forum: General Help
---

### Post by Linux-Newbie on 2007-12-20
It seems Kubuntu can detect the extra buttons but I want it to do BACK and FORWARD with them and it does something totally different, how can I get it to back and forward?

---

### Post by Existentialist on 2007-12-20
I have a logitech 5 button, and I am used to using the two side buttons as forward and back for web browsing which does not work by default in Ubuntu. I had to change my xorg.conf:

>sudo nano /etc/X11/xorg.conf

And changed:

Section "InputDevice"

    Identifier "Configured Mouse"
    Driver "mouse"
    Option "CorePointer"
    Option "Device" "/dev/input/mice"
    Option "Protocol" "ExplorerPS/2"
    Option "Emulate3Buttons" "true"

EndSection

To:

Section "InputDevice"

    Identifier "Configured Mouse"
    Driver "mouse"
    Option "CorePointer"
    Option "Device" "/dev/input/mice"
    Option "Protocol" "ExplorerPS/2"
    Option "ZAxisMapping" "4 5"
    Option "Emulate3Buttons" "true"
    Option "Buttons" "7"
    Option "ButtonMapping" "1 2 3 6 7"

EndSection

The parts in bold may be different for you, I think for my friends it was:

Option "ZAxisMapping" "6 7"
Option "ButtonMapping" "1 2 3 4 5"

Just backup the old xorg.conf before making any changes.

---

### Post by Linux-Newbie on 2007-12-21
That is the thing, the side buttons do work, I just want them set to back and forward.

---

### Post by Existentialist on 2007-12-21
> **Linux-Newbie said:**
> That is the thing, the side buttons do work, I just want them set to back and forward.

What do they do when you use them now?

---

### Post by nbayiha on 2008-04-28
i Have the same mouse, and i am experiencing some jumping problem, i mean something my mouse jump ,it often happen but it's a kind of ennoying, especially when u are playing online game.
 Do you know how to fix it?

---

