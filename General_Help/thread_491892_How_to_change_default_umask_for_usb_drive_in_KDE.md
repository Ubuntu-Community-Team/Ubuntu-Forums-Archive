---
title: "How to change default umask for usb drive in KDE?"
date: 2007-07-04
forum: General Help
---

### Post by jgonzalez on 2007-07-04
Hi there,

I have kubuntu installed, and automounting of usb flash drives is working properly (well, almost). Whenever I plug a usb drive, it gets mounted and owned by myuser:root with 755 permissions. I would like this permissions to be more restrictive, as I have my ssh and gpg keys stored in the drive, and I can't use them with these permissions.

I have been googling and searching the forums for hours and hours, and haven't been able to find a solution. It seems that KDE detects a new drive using UDEV/HAL/DBUS, and then mounts it using pmount. The default umask used by pmount for VFAT is 077, so KDE *is* changing this default, but is this hardcoded? or is this specified in some configuration file? is there any way to change it?

Thanks in advance, best regards
Jose

---

### Post by jgonzalez on 2007-07-04
I have been able to create a hal policy so all vfat file systems get a 0077 umask, but this only gets honored if I manually call pmount-hal, so I guess somebody (KDE?) is calling pmount directly using its own umask :(

---

