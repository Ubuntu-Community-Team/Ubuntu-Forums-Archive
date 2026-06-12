---
title: "Updated AMD drivers - Cannot Change Laptop Screen Brightness"
date: 2013-04-11
forum: General Help
---

### Post by abc617 on 2013-04-11
I'm actually running Linux Mint 14, but no one over there has been of any help.

So I updated my laptop's display drivers to AMD 13.1 Catalyst drivers and now I can't change my laptop screen brightness. I can still adjust the brightness slider, but the brightness settings won't take effect unless I reboot my laptop. I was able to change the screen brightness before I updated to the AMD drivers, but there were problems with the dual-monitor display set up I have.

I've tried changing the grub boot settings (acpi_backlight=vendor, acpi_osi=, acpi_osi=Linux acpi_backlight=vendor) and they don't work. I notice that when I use "acpi_backlight=vendor" that changing the brightness slider is disabled.

Any insight would be greatly appreciated!
__________________________________
Other information:
Acer V3-551
Radeon HD 7640G integrated graphics
Kernel 3.5
xorg config:
```
 Section "ServerLayout"
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
    Identifier   "0-LVDS"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1366x768"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1280x960"
    Option        "TargetRefresh" "60"
    Option        "Position" "1366 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-LVDS" "0-LVDS"
    Option        "Monitor-CRT1" "0-CRT1"
    BusID       "PCI:0:1:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   2646 2646
        Depth     24
    EndSubSection
EndSection


```

---

