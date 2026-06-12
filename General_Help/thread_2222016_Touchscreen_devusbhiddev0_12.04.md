---
title: "Touchscreen /dev/usb/hiddev0 12.04"
date: 2014-05-04
forum: General Help
---

### Post by SWTP_Tech on 2014-05-04
So I'm having an issue where a touchscreen always mounts to /dev/usb/hiddev0, and I can not for the life of me figure out why. Due to a program I am using, I would like to have the printers mount before the touchscreen, but it doesn't seem as simple as modifying a udev rule, so I am a bit lost at how proceed. Any recommendations? For reference I am using a planar touchscreen, and their drivers, with the usbtouchscreen drivers blacklisted.

Well after removing a bunch of udev rules, and commenting out xorg.conf lines, and just removing the /dev/usb/hiddev0, it seems to have no bearing on the operation of the touch screen. Currently I need to figure out how to possibly blacklist this file from being created, which i might have problems with since it is the hid module.

---

