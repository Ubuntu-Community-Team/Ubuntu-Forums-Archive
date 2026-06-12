---
title: "X VirtualDisplay not working with UXA accel method"
date: 2021-03-23
forum: General Help
---

### Post by themegax on 2021-03-23
Hi, I've been tinkering with Xorg's conf settings to create a virtual  display for VNC. However, I can't figure how to make the virtual heads  option work with the UXA accel method.
SNA works fine and creates virtual heads, but KDE elements flicker when having the mouse over.
I'm using an Intel UHD Graphics 620 integrated card and no dedicated card. Using the latest intel drivers.

Here's the content of my files:

20.intel.conf
```

Section "Device"
   Identifier "Intel Graphics"
   Driver "intel"
   Option "AccelMethod" "uxa"
   Option "TearFree" "true"
   Option "VirtualHeads" "1"
EndSection

```

xserver-xorg-video-intel/xorg.conf >> Aparently this doesn't do anything?
```

Section "Device"
    Identifier "Intel"
    Driver "intel"
    Option "AccelMethod" "uxa"
EndSection

```

[xorg.0.log]("https://paste.ubuntu.com/p/R9FYq8KdbV/") (UXA, no VIRTUAL1 output)

[xorg.0.log]("https://paste.ubuntu.com/p/zgnZymJRn5/") (SNA, has VIRTUAL1 output)

If anyone could help with either creating a virtual display with UXA or  stopping SNA from messing with the GUI elements I'll be very grateful :]

---

