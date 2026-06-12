---
title: "Resolution from command line"
date: 2007-04-09
forum: General Help
---

### Post by originof on 2007-04-09
Is it possible to set up the resolution with some commands from terminal?

---

### Post by mbeierl on 2007-04-09
Um.

Depends on what you want to do?  What, exactly are you trying to do: change the current resolution, configure the X server, etc?

---

### Post by taurus on 2007-04-09
You can edit /etc/X11/xorg.conf with

```
sudo nano -Bw /etc/X11/xorg.conf
```
or you can reconfigure it with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by simon83 on 2008-01-23
Once you have your resolutions defined in your xorg.conf file, you can switch between them using the command "xrandr -s n" where n is the ordinal of the resolution you wish to switch to. You can type "xrandr -q" to see your available resolutions and which one is currently being used.

---

### Post by Tech Provider on 2008-01-23
xrandr -s 1280x1024
-s x
This sets the screen size, either matching by size or using the index into the list of available sizes

---

