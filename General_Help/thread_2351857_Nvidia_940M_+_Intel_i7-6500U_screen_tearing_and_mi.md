---
title: "Nvidia 940M + Intel i7-6500U screen tearing and missing options in X Server Settings"
date: 2017-02-07
forum: General Help
---

### Post by hopesfall2 on 2017-02-07
[FONT=arial]Hello everyone, 

I've been pulling my hair out trying to solve the screen tearing on my latest ubuntu installation (Ubuntu Gnome 16.04).
The Laptop in question is ASUS UX303UB if that's relevant.
When i switch to the Nvidia card the screen tearing in unbearable (tearing while dragging windows, surfing the web...).

I've tried changing my xorg.conf but to no avail...
Adding: 
```

[COLOR=#000000]Option "metamodes" "nvidia-auto-select +0+0 { ForceFullCompositionPipeline = On }"[/COLOR]
[COLOR=#000000]Option "TripleBuffer" "on"[/COLOR]

```
Didn't help, it just gets ignored.

Running the below code also doesn't help:
```
nvidia-settings --assign CurrentMetaMode="nvidia-auto-select +0+0 { ForceFullCompositionPipeline = On }"

```


I'm also missing some options in the NVIDIA X Server Settings ([COLOR=#333333]Sync to Vblank)[/COLOR]:[/FONT]

[IMG]http://i.imgur.com/DYwSK4x.png[/IMG]

[IMG]http://i.imgur.com/H1lqSUk.png[/IMG]

[IMG]http://i.imgur.com/woeM6hx.png[/IMG]


[FONT=arial]my xorg.conf that gets reset to this in most cases:
```
Section "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection


Section "Device"
    Identifier "intel"
    Driver "modesetting"
    BusID "PCI:0@0:2:0"
    Option "AccelMethod" "None"
EndSection


Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection


Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "PCI:1@0:0:0"
    Option "ConstrainCursor" "off"
EndSection


Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration" "on"
    Option "IgnoreDisplayDevices" "CRT"
EndSection

```[/FONT]

---

### Post by markackerman8@gmail.com on 2017-09-29
same issue here
2-3 years later

---

### Post by Autodave on 2017-09-29
What driver are you using and where did you get it from?

---

### Post by mc4man on 2017-09-29
If using 16.03.3 (with hwe xserver) or 17.04/17.10 & a mobile nvidia gpu (optimus) then simply enable prime sync & no more tearing
[https://ubuntuforums.org/showthread.php?t=2365449](https://ubuntuforums.org/showthread.php?t=2365449)

---

