---
title: "Usb Hard drive mounts differently each boot?"
date: 2008-01-16
forum: General Help
---

### Post by CameronCalver on 2008-01-16
Hello i have a Maxtor 250gb usb hard drive and i use  this script

#!/bin/bash
rsync -av /home/server/share /media/usbdisk/backup/$(date +\%Y\%m%d)

which backs up /home/server/share to /media/usbdisk.

( im running dapper)

BUT 
Recently it was changed so bad it mounted in /media/(these weird cymbals) so i formatted the drive and did it again but now it mounts as usbdisk-1 and if i turn it off and on it mounts as usbdisk-2 and if i do a fdisk -l   it comes up as 
/dev/sdr1 
but if i turn off and on it comes as 
.dev.sds1 etc changes on letter and now if i ls /media look 

```
server@ubuntu:~$ ls /media
??    ??-2  ??-4  ??-6  ??-8   cdrom0  Maxtor   usbdisk-1  usbdisk-3  usbdisk-5
??-1  ??-3  ??-5  ??-7  cdrom  maxtor  usbdisk  usbdisk-2  usbdisk-4  usbdisk-6
server@ubuntu:~$


```

a complete mess why ?? can someone please help

---

### Post by benanzo on 2008-01-16
Go ahead and remove each of the directories that got created when you mounted the disk. Make sure you unmount the disk first though.  For safety just unplug it before removing any of those mount directories.

You should set a disk label for your disk so it will mount the same all the time, without relying on HAL to name it dynamically.  That's why you're getting all the weird mount directories.

Have a look [here]("https://help.ubuntu.com/community/RenameUSBDrive") to see how to label a disk for vfat, ext2/3, ntfs or reiser.

---

### Post by CameronCalver on 2008-01-16
if i do ls /media i get 
```
server@ubuntu:~$ ls /media
??    ??-3  ??-6  cdrom   usbdisk    usbdisk-3  usbdisk-6
??-1  ??-4  ??-7  cdrom0  usbdisk-1  usbdisk-4  usbdisk-7
??-2  ??-5  ??-8  maxtor  usbdisk-2  usbdisk-5  usbdisk-8
server@ubuntu:~$

```

but if i go sudo nautilus and go to /media i click on the folder and click delete but nothing it doesnt delete and there are no errors just nothing?

---

### Post by VON_CAPO on 2008-01-17
**benanzo** is right, follow the link he has given.
After you change the label, the disk will automatically mount with that name.  

> **benanzo said:**
> 
You should set a disk label for your disk so it will mount the same all the time, without relying on HAL to name it dynamically.  That's why you're getting all the weird mount directories.

Have a look [here]("https://help.ubuntu.com/community/RenameUSBDrive") to see how to label a disk for vfat, ext2/3, ntfs or reiser.

---

### Post by CameronCalver on 2008-01-17
yes i did that thanks heaps  it worked a treat

---

