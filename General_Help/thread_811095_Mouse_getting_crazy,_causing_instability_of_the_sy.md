---
title: "Mouse getting crazy, causing instability of the system"
date: 2008-05-28
forum: General Help
---

### Post by persistentstubborn on 2008-05-28
I run 8.04, upgraded from 7.10

For some time, the mouse is occasinally getting crazy, jumping here and there, opening windows, creating application launchers, etc. So I freqently need to reboot to get back to normal work.

sudo pico /var/log/messages 

> 

May 29 02:09:16 persistentstubborn-desktop kernel: [   60.232121] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.

So I did:

mdetect -v > /Desktop/mdetect.txt

> The mouse police never sleep.
Found the following devices:
   /dev/ttyS0
   /dev/ttyS1


How come there are two mouse devices in the system? 

I did install virtualbox today, but the problems started occuring as from installation of the system, even before the upgrade.

How do I fix that?

---

### Post by persistentstubborn on 2008-05-30
Bump.

Please help, the problem makes the system unusable. The mouse is jumping, switching throught the panels, opening windows, shutting down and generally doing all the nasty things.

I guess it's something with xorg.conf, but I don't know what to do. 

Here is cat /proc/bus/input/devices for mouse

```

I: Bus=0011 Vendor=0002 Product=0005 Version=0000
N: Name="ImPS/2 Generic Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input7
U: Uniq=
H: Handlers=mouse1 event5 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103
```

Here is cat /etc/X11/xorg.conf

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection
```

At least a link to a howto, or a manual, or something, please?

---

### Post by prshah on 2008-05-30
> **persistentstubborn said:**
> Here is cat /etc/X11/xorg.conf
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection
```
At least a link to a howto, or a manual, or something, please?

Try reconfiguring your mouse to a basic PS/2 mouse using ```
sudo dpkg-reconfigure xserver-xorg
```
==OR==
Change the above lines in xorg.conf to read:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Protocol"    "PS/2"
	Option		"Device"      "/dev/psaux"
EndSection
```

If that doesn't work, try:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Protocol"    "IMPS/2"
	Option		"Device"      "/dev/psaux"
EndSection
```

If neither of these work, try them each again one-by-one, but by commenting out the '	Option		"CorePointer"' line.

If any of these 4 combinations work, but you can't use the scroll button, add the below option in the section:```

Option "ZAxis Mapping" "4 5"

```

(Basic stuff, most probably you've already done this, but still...): If nothing works, please check the mouse in another system, or another mouse in this system. If it is a wireless mouse, check the batteries.

---

### Post by persistentstubborn on 2008-06-03
> **prshah said:**
> Try reconfiguring your mouse to a basic PS/2 mouse using ```
sudo dpkg-reconfigure xserver-xorg
```
==OR==
Change the above lines in xorg.conf to read:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Protocol"    "PS/2"
	Option		"Device"      "/dev/psaux"
EndSection
```

If that doesn't work, try:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Protocol"    "IMPS/2"
	Option		"Device"      "/dev/psaux"
EndSection
```

If neither of these work, try them each again one-by-one, but by commenting out the '	Option		"CorePointer"' line.

If any of these 4 combinations work, but you can't use the scroll button, add the below option in the section:```

Option "ZAxis Mapping" "4 5"

```

(Basic stuff, most probably you've already done this, but still...): If nothing works, please check the mouse in another system, or another mouse in this system. If it is a wireless mouse, check the batteries.

Thank you very much, I meanwhile got another mouse and it works properly. It might be a hardware problem, but I'll try your instructrions during the day and report the results.

---

