---
title: "USB Devices!?"
date: 2007-12-21
forum: General Help
---

### Post by kendalc on 2007-12-21
At one point I had SOMEHOW stumbled onto a tutorial which explained how to setup USB devices in the terminal.  Of the commands listed, one listed devices, then it used some command to assign vendor and device, and set it up.  It worked like a charm to setup the device, and (it was a controller converter) now it works with all my emulators, etc. 

However, when I encountered a game without joypad support, I used Synaptic to get joy2key, a program I used in windows on occasion.  When I try to start it from the terminal, however, it cannot find /dev/js0...  it asks if I have joypad support in my kernel.  I suspect the device is not installed to /dev/js0, and would love to see the list command that I found in that guide, but again, I can't find it.

I suspect the following command would work:
joy2key -dev (devicename)
But I don't know the name.

So... Anyone have any idea where that guide is?  Likewise, does anyone have any clue exactly which command I am referring to?  I have long since forgotten.

-thanks

---

### Post by kendalc on 2007-12-21
Okay -- browsing /dev, I remembered js0 is in the /dev/input directory.  But my command:

joy2key -dev /dev/input/js0

returns this:
...
Must specify a target!

---

