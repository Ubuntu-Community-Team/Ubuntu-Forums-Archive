---
title: "Multiple monitors with nvidia and intel on laptop...desktop spanning, why?"
date: 2014-05-22
forum: General Help
---

### Post by icest0rm on 2014-05-22
Hi all...
some weeks ago I did installed on my laptop (Dell E6520) Ubuntu new release 14.04 LTS.
After some config all was working well...

what I achieved was:

laptop on docking station, two monitors connected to nvidia card (both DVI exit of docking station) and another monitor connected to intel card (VGA exit of docking station).

the monitor are:
1. Belinea 19" 1280x1024 on the left (DVI output from nvidia)
2. Apple Cinema Display 20" 1680x1050 on the middle (DVI output from nvidia)
3. Belinea 19" 1280x1024 on the right (VGA output from intel)

all was working well...I had launcher in the middle monitor and every screen behave indipendently.

I knew that when taking laptop out from docking stantion and then in again I had some issues, mostly solved by rebooting it...but yesterday all broke up and I cannot get back to same config again!

What I reached now is more or less the same situation but everytime I move a window from the middle display to the left or to the right, the screen (unity dock etc.) moves too shifting...

example, I move one window from the apple display to the belinea right of it and the unity dock (which was at the left of the apple display) start shifting to the left belinea screen along with the background and icons that were in the apple display...and what was at the left side of the left belinea just disappear out of the screen....dunno why and how to fix...anyone can give me any hint?

also the strange part is that when I try to maximize a window, it goes spanned between apple display and belinea in its right (intel card).

this is xorg.conf:

Section "ServerLayout"
Identifier "layout"
Screen 0 "nvidia"
Inactive "intel"
EndSection

Section "Device"
Identifier "intel"
Driver "modesetting"
BusID "PCI:0@0:2:0"
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
EndSection


first time i had setup all, all I did use was display settings in Ubuntu control center.
now I've looked into:

- xorg.conf
- .config/monitors.xml
- nvidia-settings
- xrandr

but I still don't understand where settings are placed and which is the correct place to edit them.

Thanks

---

