---
title: "Configuring mouse buttons on Logitech MX600--problems with evdev?"
date: 2008-03-14
forum: General Help
---

### Post by brnetonboy on 2008-03-14
Hi, I just installed 7.10 Gutsy Gibbon yesterday. I've tried Linux several times before, but I've always encountered too many hurdles and gone back to Windows. 

I have a Logitech MX600 or MX610 and I want the thumb buttons and top buttons to work. But Ubuntu doesn't seem to have a way to configure my mouse--or else it needs a drive (or is that a Windows concept??).

Anyway, I have been trying to follow these tutorials but having trouble. Hopefully these tutorials aren't leading me down the wrong road!

[http://ubuntuforums.org/showthread.php?t=65471&highlight=mx600](http://ubuntuforums.org/showthread.php?t=65471&highlight=mx600)

Following that tutorial, I make it as far as doing the edit, and restarting X. But then Ubuntu goes into low graphics mode until I revert the changes back. 

This is what I put in: (not sure what the problem is)

```

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "Protocol"        "evdev"
    Option        "Dev Name"        "Logitech USB RECEIVER"
    Option        "Dev Phys"        "usb-*/input0"
    Option        "Device"          "/dev/input/event3"
    Option        "Buttons"         "10"
    Option        "ZAxisMapping"    "4 5"
EndSection

```

The other thing I think might be the problem is I don't think evdev is installed... I searched for it with Synaptic Package Manager but it didn't show up! I was reading in 
[this other tutorial]("http://ubuntuforums.org/showthread.php?t=219894&highlight=logitech+mouse+mx600")
 that the way to install evdev is to run this line:

```
sudo apt-get install xserver-xorg-input-evdev
```

but it gives me this!

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-org-input-evdev

```

gaa... I eventually want to be able to follow the directions on this tutorial: 

[http://ubuntuforums.org/showthread.php?t=332256&highlight=mx600](http://ubuntuforums.org/showthread.php?t=332256&highlight=mx600)

but I'm not even clear if that is ultimately going to get me what I want. Namely, I want to assign different things for my mouse buttons. Any help from anyone is greatly appreciated! Thanks !!

---

