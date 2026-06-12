---
title: "Want to use most basic graphics mode"
date: 2008-02-29
forum: General Help
---

### Post by Jethro_uk on 2008-02-29
Following problems with an old MSI6309 motherboard and old ATI Radeon (no idea of model) AGP graphics card not running the LiveCD, I managed to successfully run the alternative text install.

However, upon boot, I'm getting the same issue as the LiveCD - it gets so far, then shuts down.

On the basis I got Knoppix to work, I suspect it's the ATI driver (or lack thereof).

Given that this PC is going to act as a small download server, and I only really want Ubuntu to be able to use the gtkndis package to get my wireless USB dongle working, is there an easy way to force Ubuntu to use a standard, low res (640x480, 800x600) video mode ?

I can get in through recovery mode, so is it as simple as editting a file ? Deleting xorg.conf ?

---

### Post by kesman on 2008-02-29
edit the /etc/X11/xorg.conf file.
In there you should find a section with resolutions in it. Edit it so that the highest resolution would be 800x600.

---

### Post by zvacet on 2008-02-29
```
 cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

```
dpkg-reconfigure xserver-xorg
```

when you come to the drivers select **vesa **and continue to the end.After restart you should have basic graphic.Later you can search for your video card driver.

---

