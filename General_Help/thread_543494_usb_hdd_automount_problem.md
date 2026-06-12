---
title: "usb hdd automount problem"
date: 2007-09-05
forum: General Help
---

### Post by klep on 2007-09-05
Hello, 

I have read several topics on this but haven't found a solution as yet.

I have a usb harddrive which used to automount completely correctly. Now it doesn't. Doing lsusb when it is plugged in shows that it is being detected, and if i manually mount it (sudo mount -t vfat /dev/sdc1 /media/usbHDD) then I can get readonly access to it. There are no entries in fstab for it.

Does anyone know how I can get this automounting correctly again? From what I understand I should not be putting it in fstab as that is for permanent harddrives.  The mountpoint should be created dynamically by ubuntu when I plug it in. Does anyone know how I can get this behavior back? 

Thanks alot.

---

### Post by agemon on 2007-09-05
> **klep said:**
> 
From what I understand I should not be putting it in fstab as that is for permanent harddrives.  The mountpoint should be created dynamically by ubuntu when I plug it in. 

don't know about that, i have mine in fstab and it has never given an error. here's my fstab entry:
```

/dev/sdb	/mnt/usb	auto	rw,user,noauto	0	0

```
the usb stick is in /dev/sdb, and i have a folder /mnt/usb in which i want to mount it.

---

### Post by vanadium on 2007-09-05
Should certainly not be in fstab. The reason of the odd behaviour might be errors on the vfat file system. Check the drive first as I described here [http://ubuntuforums.org/showthread.php?t=540318&page=2](http://ubuntuforums.org/showthread.php?t=540318&page=2) to rule out this possibility.

---

### Post by klep on 2007-09-05
hi guys, 

thanks for your help. I just went through the dosfsck process. It complained that the bootsector of the drive was different from the backup boot sector. I selected to restore the backup but it would appeart to be actioning it for a while and then nothing would change. 

I gave up. The data on there wasnt important (i use the drive purely to backup stuff) so I simply took it to my XP machine and reformatted the drive as NTFS. All is working now.


Thanks for your help.

---

