---
title: "Xrandr/xorg.conf Custom Resolution"
date: 2014-04-06
forum: General Help
---

### Post by jake31 on 2014-04-06
I am trying to add a custom resolution, which is 1910x1006. When I type cvt 1910 1006, and I get: 

[B]1912x1006 59.96 Hz (CVT) hsync: 62.60 kHz; pclk: 159.75 MHz
Modeline "1912x1006_60.00"  159.75  1912 2032 2232 2552  1006 1009 1019 1044 -hsync +vsync[/B]

Which is OK, I can work with this if I have too, but I cannot for the life of me get this custom resolution to add to my screen, labeled "DVI-D-0"

The --newmode command seems to have worked, and the custom resolution is visible under:

[B]DP-1 disconnected (normal left inverted right x axis y axis)
  1912x1006_60.00 (0x2d2)  159.8MHz[/B]

When I try --addmode I get this:

[B]xrandr --addmode DVI-D-0 1912x1006_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  41
  Current serial number in output stream:  42[/B]

What am I doing wrong? Thanks!

---

