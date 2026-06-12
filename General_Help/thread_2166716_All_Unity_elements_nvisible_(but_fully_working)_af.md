---
title: "All Unity elements nvisible (but fully working) after Catalyst 13.8 Beta install"
date: 2013-08-10
forum: General Help
---

### Post by ProfessorLe on 2013-08-10
Hi, my main OS is/was Debian Testing, but I had even more trouble with this driver over there, and I had a spare hard drive. I installed Ubuntu 13.10 with the normal / and /home and swap setup.

My problems began after installing the driver, and I'm utterly confused as to what's going on. When I login to my account, Unity appears to not load, but the desktop is right clickable. The shadow from the top panel is also visible, which lead to my discovery that Unity was 100% functional but also 100% invisible. Everything generally performs great, you can open anything from the dock, but the dock and panel (and search if you bring it up) are invisible.

Here's where it gets interesting, for the heck of it I Ctrl+Alt+F2'd my way into a root terminal and ran startx and Unity works perfectly in root.

Any advice is appreciated, the GPU in question is a Radeon HD 5770. Deleting ~/.drirc didn't work.

Here's my xorg.conf:
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

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

---

