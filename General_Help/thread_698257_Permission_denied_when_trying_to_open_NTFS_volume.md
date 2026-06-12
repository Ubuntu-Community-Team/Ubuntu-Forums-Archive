---
title: "Permission denied when trying to open NTFS volume"
date: 2008-02-16
forum: General Help
---

### Post by zander8807 on 2008-02-16
When I try to open an NTFS volume I receive this error in Dolphin:

An error occurred while accessing 'Volume (ntfs)', the system said: org.freedesktop.Hal.Device.PermissionDeniedByPolicy: hal-storage-fixed-mount-all-options refused uid 1000.

This seems like it would be a common error that a new linux user would run into, however I didn't find any info in the forums. Any help would be appreciated!

---

### Post by ESPOiG on 2008-02-16
is the NTFS harddrive a local one, just the error you got there has url?

and have you tried sudo ' ing it, like gksu nautilus and then accessing it?

--

sorry i didnt realise you were using dolphin :D try running dolphin as sudo and see what happens

---

### Post by TheWizzard on 2008-02-16
> **zander8807 said:**
> When I try to open an NTFS volume I receive this error in Dolphin:

An error occurred while accessing 'Volume (ntfs)', the system said: org.freedesktop.Hal.Device.PermissionDeniedByPolicy: hal-storage-fixed-mount-all-options refused uid 1000.


in the properties of the device under mout there is "mount as user". uncheck that box and you can mount it.

---

### Post by Nephus on 2008-02-18
> **TheWizzard said:**
> in the properties of the device under mout there is "mount as user". uncheck that box and you can mount it.
I have the same problem.  I unchecked the box, ran dolphin with sudo, still get the error.  Any other suggestions?

---

### Post by housam on 2008-02-18
> **zander8807 said:**
> When I try to open an NTFS volume I receive this error in Dolphin:

An error occurred while accessing 'Volume (ntfs)', the system said: org.freedesktop.Hal.Device.PermissionDeniedByPolicy: hal-storage-fixed-mount-all-options refused uid 1000.

This seems like it would be a common error that a new linux user would run into, however I didn't find any info in the forums. Any help would be appreciated!

Try to mount the volume ntfs ( as in ubuntu using [[COLOR="black"][COLOR="black"][COLOR="Red"]this guide [/COLOR][/COLOR][/COLOR]]("https://help.ubuntu.com/community/MountingWindowsPartitions")-  I don't know how in Dolphin ) it may help

---

