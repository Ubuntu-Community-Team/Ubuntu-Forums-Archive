---
title: "saving to a usb in root"
date: 2007-04-24
forum: General Help
---

### Post by jdwood83 on 2007-04-24
I tried installing Beryl on my laptop (Compaq Evo), long story short: my computer couldn't handle it and now i have no graphical interface (root only).  I aim to reinstall Feisty with the CD I have, but I have two document files I would like to save to my USB device before doing so.  I spent the last 2 hours trying to find out how to copy the two files from the Desktop folder to the USB entirely in root (I can't even find my USB device folders), but to no avail.  Any help would be greatly appreciated!!

JDWood

---

### Post by disturbedite on 2007-04-25
well, for simplicity, i would just say to do this from console:
sudo cp /path/to/my/file /path/to/my/usbdrive

but since you can't find your usb drive, that obviously takes first priority.  there is a command ls -l [SIZE=-1]/dev/disk/by-uuid/ to view your devices by uuid, but unless you *do* have them assigned by uuid the only thing i can tell you is to try to find out the alternative command of that.  in other words, how to view the devices other than by uuid.
[/SIZE]

---

