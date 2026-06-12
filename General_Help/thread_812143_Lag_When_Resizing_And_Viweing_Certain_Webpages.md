---
title: "Lag When Resizing And Viweing Certain Webpages"
date: 2008-05-29
forum: General Help
---

### Post by solarwind on 2008-05-29
Hey all.

I have an nVidia 8800GT card, an Athlon X2 4400+ processor and 2GB of DDR2 800 RAM. I'm using the latest nVidia drivers, but this didn't help to fix the problem either.

My problem is: I have a LOT of lag when resizing windows and scrolling through certain webpages. My hardware can handle simple tasks like this for sure. It works perfectly in winbloze. I'm using XFCE as a window manager. Is there any way to solve this problem?

---

### Post by unutbu on 2008-05-29
I'm guessing there may be something improperly configured in your xorg.conf. Please post:

```
cat /etc/X11/xorg.conf | perl -ne "print unless (m/^#/)"
```

---

### Post by solarwind on 2008-05-29
> **unutbu said:**
> I'm guessing there may be something improperly configured in your xorg.conf. Please post:

```
cat /etc/X11/xorg.conf | perl -ne "print unless (m/^#/)"
```

Here it is: ```
vg@vg-x2 ~ $ cat /etc/X11/xorg.conf | perl -ne "print unless (m/^#/)"

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
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
    Driver         "keyboard"
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
    Option         "RenderAccel"
    Option         "BackingStore"
    Option         "DamageEvents"
    Option         "TripleBuffer"
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

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

Just a heads up, I'm not using Ubuntu, I'm using Arch Linux. However, that shouldn't make too much of a difference, Linux is Linux.

---

### Post by unutbu on 2008-05-29
Have you read [http://wiki.archlinux.org/index.php/NVIDIA?](http://wiki.archlinux.org/index.php/NVIDIA?)

Following advice found on that page, have you tried checking 
```
glxinfo | grep direct
glxinfo | egrep "glx (vendor|version)"
```

Also, I'm not sure if this makes a difference, but 
I wonder if 

```
    Option         "RenderAccel"
    Option         "BackingStore"
    Option         "DamageEvents"
    Option         "TripleBuffer"
```
should be
```
    Option         "RenderAccel" "True"
    Option         "BackingStore" "True"
    Option         "DamageEvents" "True"
    Option         "TripleBuffer" "True"
```

If that doesn't work, I suggest you do a series of experiments: Comment out each of the following one by one
```

    Load           "dbe"
    Load           "extmod"
    Load           "freetype"
    Option         "RenderAccel"
    Option         "BackingStore"
    Option         "DamageEvents"
    Option         "TripleBuffer"
    Option         "Composite" "Enable"
```

(In theory, there are 63 experiments in all). I suspect if you disable enough of them, your current problem will go away, though you might also lose some feature you want. Still, with enough of these experiments you might be able to isolate the problem line. 

Sorry I don't have deeper knowledge. Perhaps another reader will have better advice.

---

### Post by solarwind on 2008-05-29
Yes, I have read their wiki. No difference. Besides, that wiki page is quite old.

---

### Post by solarwind on 2008-05-30
Can anyone please help?

---

### Post by Zorael on 2008-05-30
**xserver-xgl** package installed? If so, nuke it.

---

### Post by solarwind on 2008-05-30
> **Zorael said:**
> **xserver-xgl** package installed? If so, nuke it.

Not installed.

---

