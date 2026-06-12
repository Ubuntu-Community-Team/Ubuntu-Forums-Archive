---
title: "MS Wireless Notebook 4000 Mouse"
date: 2008-03-05
forum: General Help
---

### Post by Tristam Green on 2008-03-05
Where to begin...

This mouse.  It's a great little mouse, but I cannot get the side-scrolling to work correctly at all.

I'd like, as an added bonus, to get the thumb button bound to the Zoom feature in Compiz, but I'll work on that later.

Before anyone says it, I've referenced the following, and each to no avail:

[Phynix's thread.]("http://ubuntuforums.org/showthread.php?t=558250")

[Delfick's Thread.]("http://ubuntuforums.org/showthread.php?t=577594")

[DeltaNova how-to]("http://www.deltanova.co.uk/497/")

[Gentoo Wiki's Xorg How-To.]("http://gentoo-wiki.com/HOWTO_Advanced_Mouse")



What happens is any time I make a change in xorg.conf, I get the wonderful "black screen, white cursor" deal, and have to open the recovery mode to set it back...

For posterity, here's what xorg.conf's InputDevices section and Server Sections look like when stable (mouse works, no side scrolling).

```
Section "InputDevice"
[INDENT]Identifier  "Configured Mouse"[/INDENT]
[indent]Driver    "mouse"[/indent]
[indent]Option   "CorePointer"[/indent]
[indent]Option   "Device"     "/dev/input/mice"[/indent]
[indent]Option   "Protocol"   "ImPS/2"[/indent]
[indent]Option   "ZAxisMapping"        "4 5"[/indent]
[indent]Option   "Emulate3Buttons"   "true"[/indent]
EndSection

Section "InputDevice"
[INDENT]Identifier   "Synaptics Touchpad"[/INDENT]
[indent]Driver    "synaptics"[/indent]
[indent]Option   "SendCoreEvents"   "true"[/indent]
[indent]Option   "Device"   "/dev/psaux"[/indent]
[indent]Option   "Protocol"   "auto-dev"[/indent]
[indent]Option   "HorizEdgeScroll"   "true"[/indent]
[indent]Option   "SHMConfig"   "on"[/indent]
EndSection

```

```
Section "ServerLayout"
[. . .]
[indent]Inputdevice   "Configured Mouse"[/indent]
[indent]Inputdevice   "Synaptics Touchpad"[/indent]
[. . .]
EndSection

```

Here is cat /proc/bus/input/devices:

```
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

[. . .]

I: Bus=0003 Vendor=045e Product=00e1 Version=0111
N: Name="Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00"
P: Phys=usb-0000:00:13.1-1/input0
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=1c3
[. . .]
```

Any help would be awesome, because it's driving me bonkers not being able to get this right.

---

### Post by Tomatz on 2008-04-07
Yeah i've still had no luck with my wireless laser mouse 5000 :(

---

### Post by Tristam Green on 2008-04-07
> **Tomatz said:**
> Yeah i've still had no luck with my wireless laser mouse 5000 :(

Heh, I'd forgotten about this thread, and fully understand how you found it ;)

I'd tried a lot of xorg.conf editing and hosed my system to the point of doing a rebuild, and I still haven't made any headway with this whatsoever.

---

