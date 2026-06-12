---
title: "Mouse giving problems"
date: 2008-07-05
forum: General Help
---

### Post by vidur on 2008-07-05
I have a new laptop and I'm trying to install Ubuntu on it. The in-built mouse is not working on Ubuntu...do you have to install device drivers or something in ubuntu?

Would using an external mouse help my cause?

---

### Post by mempman on 2008-07-05
An external mouse would help.

However, in order to get your internal mouse to work, I would suggest that you post your /etc/X11/xorg.conf file here.

Within this file, you should have individual sections for each of you "Input Devices"...look at mines for example.


```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
    Option         "SHMConfig" "on"
EndSection

```

---

### Post by vidur on 2008-07-05
Would i get that file in Windows or I'l have to use linux only for that?

---

### Post by mempman on 2008-07-05
> **vidur said:**
> Would i get that file in Windows or I'l have to use linux only for that?

That file is in your linux partition.  It probably resides in /etc/X11/

and it is called xorg.conf.

To see the contents of this file:

Open gedit, open files, /etc/X11/xorg.conf

---

### Post by vidur on 2008-07-06
But I havent partitioned yet or for that matter installed Ubuntu also as it was impossible to do it w/o the mouse working.

I'l install with the external mouse and then get that file to make the internal mouse work...right?

---

### Post by jespdj on 2008-07-06
With "internal mouse", do you mean the touchpad?

What brand and model is your laptop and what version of Ubuntu are you using? These details are important.

On my Dell XPS M1530 for example, I have to add a kernel parameter when booting Ubuntu to make the touchpad work properly. But that's only for this particular laptop model and Ubuntu 8.04.

---

### Post by vidur on 2008-07-07
Coincidentally, even mine is a Dell XPS 1530. with Ubuntu 8.04..ya, i mean the touchpad

---

