---
title: "Very slow dual monitor on Ubuntu 12.10 w/ATI FirePro v4900"
date: 2013-06-05
forum: General Help
---

### Post by bdemchak on 2013-06-05
Hi, all --

I'm fairly inexperienced with Ubuntu (v12.10, newly installed from scratch), but have gotten as far as loading AMD's latest (I think) drivers for the FirePro v4900 (i.e., Radeon).

The workstation is brand new ... 4 core 3.3GHz, 64GB RAM ... one monitor is DVI-D and the other is DisplayPort. Both are Dell U2713H monitors.

When I'm using just one monitor, very snappy window displays and menu dropdowns.

When I'm using two monitors, very slow window displays and I can watch the menu dropdowns animate in sloooow real time. And the mouse gets agonizingly jerky.

Any idea what's causing this?? Or even where to look??

ATI's Catalyst Control Center Information shows Driver Packaging Version 9.00.11-120920a-147436C-ATI, and 2D driver version 9.0.2. OpenGL version is 4.2.11903.

The contents of /etc/X11/xorg.conf is below ...

Thanks for any help you can give!

(This looks suspiciously like an old thread that was closed ... but without resolution: 
[http://ubuntuforums.org/showthread.php?t=1743667&page=8&highlight=slow+radeon+dual+monitor](http://ubuntuforums.org/showthread.php?t=1743667&page=8&highlight=slow+radeon+dual+monitor))


> Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "0-DFP5"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "2560x1440"
    Option        "TargetRefresh" "60"
    Option        "Position" "2560 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-DFP9"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "2560x1440"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP5" "0-DFP5"
    Option        "Monitor-DFP9" "0-DFP9"
    BusID       "PCI:3:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   5120 2560
        Depth     24
    EndSubSection
EndSection

---

