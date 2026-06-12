---
title: "Widescreen Resolution Issue"
date: 2007-12-21
forum: General Help
---

### Post by Parag2k3 on 2007-12-21
I just got a new monitor which has a native resolution of 1680x1050 but I can't get the display to work correctly. Whenever I try to use that resolution, the actual resolution is 800x600 and I have to scroll to see the whole screen. It seems to do this for only widescreen resolutions. I've used both the Screens and Graphics utility as well as editing xorg.conf

Its a Acer X203W and is connected by VGA
H-Frequency 30-83
V-Frequency 55-75
and the native resolution is 1680x1050 at 60Hz

Using integrated intel graphics, Screens and Graphics says its an Intel 845 and is using the  i810 driver.

Any ideas?

-edit
> Intel 800/900 Series VBIOS Hack : version 0.5.3

Chipset: 845G
BIOS: TYPE 3
Mode Table Offset: $C0000 + $4d2
Mode Table Entries: 25

Mode 30 : 640x480, 8 bits/pixel
Mode 31 : 640x400, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 40 : 640x480, 15 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 42 : 800x600, 15 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 44 : 1024x768, 15 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 48 : 1280x1024, 15 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4a : 1600x1200, 15 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4c : 1920x1440, 15 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel


> #
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=5c
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=1680
YRESO=1050
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
BIT=32

-edit 2
Looks like I missed a X restart, its working fine now

---

