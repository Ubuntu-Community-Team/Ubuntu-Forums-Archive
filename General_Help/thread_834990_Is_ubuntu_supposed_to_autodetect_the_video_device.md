---
title: "Is ubuntu supposed to autodetect the video device?"
date: 2008-06-20
forum: General Help
---

### Post by Methuselah on 2008-06-20
I ask if it's supposed to autodetect because my default xorg.conf is extremely bare bones.

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

```

The device sections says nothing at all (makes no mention of my ati card).
I this a bug?

I'm going to try to fix this by running X -configure but I need to not have X running. I figure if I reboot into a recovery mode I MAY be able to do this. Alternatively, how do you turn off gdM in ubuntu? BSD and Archlinux have an rc.conf system but I don't know what's equivalent in ubuntu.

Thanks.

---

### Post by pauper on 2008-07-19
```
sudo dpkg-reconfigure xserver-xorg
```

Note: You can try VESA driver in case ATI is absent or don't work properly.

> BSD and Archlinux have an rc.conf system but I don't know what's equivalent in ubuntu.
Ubuntu uses upstart.

[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

Do disable GDM run this:

```
sudo mv /etc/rc2.d/S30gdm /etc/rc2.d/K30gdm
```

Note: Keep your own number if it's different than "30"; the goal is to replace
"S" for "K".

---

