---
title: "Help needed after kernel upgrade to 2.6.17-11"
date: 2007-02-18
forum: General Help
---

### Post by Cariboo1938 on 2007-02-18
Help needed- 
After kernel upgrade to 2.6.17-11-generic,  I can't access my Windows NTFS anymore.
**Facts:**
```
sudo fdisk -l | grep NTFS
``` gives this: > /dev/sdb1   *           1        4717    37889271    7  HPFS/NTFS      # Windows XP
/dev/sdb2            4718       14946    82164442+   7  HPFS/NTFS     # Windows User
**If I try to mount WinUser** as root@BitByter:
 ```
sudo mount WinUser
```I get the prompt
> mount: can't find WinUser in /etc/fstab or /etc/mtab despite entries > /etc/fstab: /dev/sdb2    /media/WinUser  ntfs-3g   defaults,locale=en_US.utf8   0  0 
/etc/mtab:/dev/sdb2 /media/WinUser ntfs-3g rw 0 0
**Other facts:**
Directory "/media/WinUser" exists! and package "ntfs-3g" is installed!
Any help or hint or idea is highly appreciated!

---

### Post by K.Mandla on 2007-02-18
Would [this]("http://www.ubuntuforums.org/announcement.php?f=140") be at all related to your problem? 

Aside from that, I've never used ntfs-3g, so I'm afraid I can't be of much help. :( Sorry.

---

### Post by solar george on 2007-02-18
Reinstall the ntfs-3g driver.

Try with the old read only driver - just see if it works.

Sit tight and wait for an update to ntfs-3g

---

