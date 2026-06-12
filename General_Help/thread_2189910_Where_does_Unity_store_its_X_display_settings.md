---
title: "Where does Unity store its X display settings?"
date: 2013-11-24
forum: General Help
---

### Post by meta_qoph on 2013-11-24
I am dual-booting Ubuntu and Gentoo on my machine, and (surprise) having trouble with X configuration under Gentoo. (The specific problem is that, even with the correct resolution set, the display on my external monitor does not fill the whole screen -- it leaves about 3 cm black at the bottom and at the right. Incidentally, if anyone knows what's causing that, I'd appreciate it, because I've not been successful in googling for further information.) I was able to configure my displays properly through Unity on Ubuntu, and I would like to copy my X configuration from Ubuntu to Gentoo, but I can't find where this configuration is stored. My understanding is that X configuration settings are stored either in a file named "xorg.conf" or in a directory named "xorg.conf.d" in various possible locations, but:

```

$ locate xorg.conf
/usr/share/X11/xorg.conf.d
/usr/share/X11/xorg.conf.d/10-evdev.conf
/usr/share/X11/xorg.conf.d/11-evdev-quirks.conf
/usr/share/X11/xorg.conf.d/11-evdev-trackpoint.conf
/usr/share/X11/xorg.conf.d/50-synaptics.conf
/usr/share/X11/xorg.conf.d/50-vmmouse.conf
/usr/share/X11/xorg.conf.d/50-wacom.conf
/usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf
/usr/share/man/man5/xorg.conf.5.gz
/usr/share/man/man5/xorg.conf.d.5.gz

```

and those files only address input devices, not displays. Where should I look for my display settings? Thanks.

---

