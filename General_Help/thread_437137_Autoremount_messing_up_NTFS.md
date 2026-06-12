---
title: "Autoremount messing up NTFS"
date: 2007-05-08
forum: General Help
---

### Post by csulok on 2007-05-08
Hey there

I'm using Ubuntu Feisty with all the system updates and no 'hax' done in any part of it so far ;)
I have an external HDD connecting through USB2, it has NTFS on it in a single partition.
I have automount on hot-plugged drives enabled in the system preferences.

Whenever I want to disconnect the drive I click on eject on the context menu of the mountpoint ( using the icon on the desktop ) or on disconnect in Gnome Commander and I get the 'It is now safe to remove the drive' message but than it immediately remounts the drive correctly.
Is there a way to disable autoremounting after such an eject?

If i just disconnect the drive either by powering it down, or unplugging the USB cable I'll get error messages in Windows XP and I have to do chkdsk before I can use it properly again. (Same goes for Windows, if I simply unplug the drive without using the eject feature, I'm getting error messages in Linux which prompt me to use ntfsfix.. but only chkdsk helps save forced mounting.. )

As a temporary solution I always have to disable automount on hotplugged devices in the system preferences before ejection, and enable it before I want to use the HDD again, which is tbh more annoying than the issue itself.

Any input would be very appreciated, thank you

---

### Post by csulok on 2007-05-09
shameless bump because its really annoying :(

---

### Post by soro2005 on 2007-05-17
In case you haven't found that solution yet: Try unmounting manually, works for me:
```
sudo eject /media/WhateverYourDriveIsMountedAs
```
in a Terminal. I don't have a clue what's different from right click-->unmount here, other than it's the superuser. But that might be the point. Wouldn't be the first time superuser can do things we commoners can not ;-) Or perhaps it's also in the eject vs. unmount.

---

### Post by csulok on 2007-05-18
thank you, i'll check it asap.

edit: thank you, it's working \o/ \o/

---

