---
title: "custom icons for multiple devices in Nautilus"
date: 2012-11-26
forum: General Help
---

### Post by dragonfly41 on 2012-11-26
I'm running Ubuntu 12.04 LTS (32 bit)

In Nautilus the icons under Devices are all the same grey style.
Usually  I have quite a number of different partitions on external devices to navigate through.
Is it possible to customise these Nautilus devices icons?
Even the same icon with different colours would be useful.

Would adding an autorun.inf file to each device point to a custom icon?
I've looked at System tools > Preferences > Removable Drives and Media
and ticked "autorun programs on new drives and media"
and added a test autorun.inf file and icon to autorun folder at root of one device ..

but I don't see any change in icon.

---

### Post by elliotn on 2012-11-26
I don't know about devices but I changed my by overwriting them

---

### Post by dragonfly41 on 2012-11-26
Thanks

I just found that the autorun.inf approach works .. after inserting the autorun.inf file pointing to the custom icon I had to unmount the device and then remount the device.   The custom icon is seen under Devices.

---

### Post by elliotn on 2012-11-26
I don't know about devices but I changed my by overwriting them

---

