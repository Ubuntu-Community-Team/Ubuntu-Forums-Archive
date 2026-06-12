---
title: "unable to start firestarter gtk-warning"
date: 2007-03-13
forum: General Help
---

### Post by TDK800 on 2007-03-13
Installed beryl, couldn't get it to work, actually couldn't boot, so restored system with the command described in x11/xorg.conf to VGA as screen... I'm not sure what graphics card I have to set it to VGA, intel chipset graphics i think... so maybe related to this?


sudo firestarter
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:5648): Gtk-WARNING **: cannot open display:

---

### Post by TDK800 on 2007-03-13
I've tried running the "sudo dpkg-reconfigure -phigh xserver-xorg", but not sure which option to choose, currently running with VESA 1024x768, it loads up Gnome, but firestarter won't start.

Device Manager says my notebook uses:
82852/82855 Integrated Graphics Device (by Intel Corporation)
82852/82855 GM/GME/PM/GMV Processor to I/O Controller (by Intel Corporation)

There's no intel option under the xserver re-configuration, VGA doesn't work either.

---

### Post by TheWizzard on 2007-03-13
try:
gksudo firestarter

---

### Post by TDK800 on 2007-03-13
still same error

---

### Post by Ramses de Norre on 2007-03-13
What's the result after running ```
sudo xhost +
```

---

### Post by bapoumba on 2007-03-13
Do you get the same error to **gksudo gedit** ?

---

