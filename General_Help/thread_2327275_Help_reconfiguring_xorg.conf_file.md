---
title: "Help reconfiguring xorg.conf file"
date: 2016-06-09
forum: General Help
---

### Post by Rohit_Dnyansagar on 2016-06-09
Hello,
I have Asus laptop with two external screens one with VGA and one with DVI. They were working fine but recently I changed some settings and now when I connect both of them I get no signal on the screens. However if I connect either one of them, it works fine, I dont understand the problem. Here is how my xorg.conf file looks like
```
Section "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection

Section "Device"
    Identifier "intel"
    Driver "intel"
    BusID "PCI:0@0:2:0"
    Option "AccelMethod" "SNA"
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
```


.....Thanks

---

### Post by ajgreeny on 2016-06-09
Please use **Code-Tags** for terminal output and code. See my signature below for a **How-to**

---

### Post by oldos2er on 2016-06-09
Moved to General Help.

---

