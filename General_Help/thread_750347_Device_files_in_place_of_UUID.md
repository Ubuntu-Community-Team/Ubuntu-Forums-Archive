---
title: "Device files in place of UUID"
date: 2008-04-09
forum: General Help
---

### Post by ravi.xolve on 2008-04-09
I use Kubuntu. I want to use device files in place of UUIDs as working with debain I have been familiar with them I tried changing the settings from the System Settings for disks, but system still uses UUIDs.
Even theusb drives are used by UUIDs and I even don't see options for that. Please help me in this matter.

---

### Post by munkyeetr on 2008-04-09
If you know what device it is, you can just replace the UUID with the path to the device.

For instance, in fstab, use /dev/<device> in place of the UUID.

---

