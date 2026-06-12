---
title: "some problems after nvidia driver upgrade"
date: 2008-03-06
forum: General Help
---

### Post by svtfmook on 2008-03-06
after upgrading to the latest nvidia driver, i've been having problems with desktop effects.

#1, title bar buttons.
it first started when i try to enable pixmap buttons in emerald.

#2, disappearing title bar
when i'm writing an email with swiftdove, every keystroke turns on, then off the title bar.

any ideas?

---

### Post by Meow27 on 2008-03-06
it would be helpful to tell us what graphics card u have

---

### Post by overdrank on 2008-03-06
Hi and you may try this command
```
sudo nvidia-xconfig --allow-glx-with-composite
```
if this fails then try to add
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
To you device section in the xorg, example below


```
Section "Device"
Identifier "nVidia Corporation NV11DDR [GeForce2 MX200]"
Driver "nvidia"
BoardName "nv"
BusID "PCI:1:0:0"
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
Screen 0
EndSection
```

But first backup your xorg with this
To copy Xorg


```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```

To restore backup

```

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

You can edit the xorg with this command

```

gksudo gedit /etc/X11/xorg.conf
```

Then save the file and restart x with the ctrl, alt, backspace keys or restart the system.

---

