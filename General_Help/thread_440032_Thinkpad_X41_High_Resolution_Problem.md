---
title: "Thinkpad X41 High Resolution Problem"
date: 2007-05-11
forum: General Help
---

### Post by scott.k.moore on 2007-05-11
I'm running Feisty and I have an IBM X41 laptop with an Intel 915GM graphics chip...   and I can't seem to get any resolution above 1024x768.  I've read a number of different attempts at this problem, but so far nothing has fixed my issue.  The issue is this:

When I'm using the laptop in stand-alone mode I'm fine with the 1024x768 resolution, but when I'm in the office using my external monitor I need a higher resolution available.  Ideally, I'd like to have the laptop boot automatically into 1024x768 when it's stand-alone, but then be able to switch it manually (or automatically if possible) to a much higher resolution (1600x1200) when I use the external monitor.    

Here's what I've done so far:

1.  Installed the 915resolution package.
2.  Applied the 915resolution package.... and modified the /etc/default/915resolution file as indicated with my desired resolution option (Mode 5a, 1600x1200, 32 bits/pixel)
3.  Modified my xorg.conf to include the display mode above.
4.  Run the 915resolution "/etc/init.d/915resolution start"  and get:

Chipset: 915GM
BIOS: TYPE 1
Mode Table Offset:  $C0000 + $269
Mode Table Entries:  36

Patch mode 5a to resolution 1600x1200 complete
915resolution.

5.  Restart X11 and still only have 1024x768 as a resolution option.

Any help would be greatly appreciated!

Scott K.****

---

