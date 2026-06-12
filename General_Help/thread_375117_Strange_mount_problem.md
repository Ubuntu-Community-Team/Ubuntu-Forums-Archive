---
title: "Strange mount problem"
date: 2007-03-03
forum: General Help
---

### Post by PaulFXH on 2007-03-03
Edit:
This is now resolved. Problem was due to "typo" in the fstab entry for SCSI0_VOL4

My external (usb) HD has four partitions (and another which is an extended partition) named:
SCSI0_VOL1
SCSI0_VOL2
usbdisk
SCSI0_VOL4

 All but usbdisk (ext3) are formatted to ntfs. 

I have used this HD for quite some time in both Ubuntu and virtual WinXP without any serious problems.
However, yesterday, I neglected to "safely remove hardware" on the external HD before shutting down the virtual WinXP (VMware Player). As a result, only the icon for usbdisk appeared on the Ubuntu desktop today.

So, I re-created the folders SCSI0_VOLx (x=1,2 or 4) in /media (all had dissappeared) and included the following lines in /etc/fstab:
```
/dev/sda1       /media/SCSI0_VOL1    ntfs defaults,nls=utf8,umask=022   0       0
/dev/sda5       /media/SCSI0_VOL2  ntfs defaults,nls=utf8,umask=022  0       0
/dev/sda7       media/SCSI0_VOL4  ntfs defaults,nls=utf8,umask=022  0       0

```

While this gives an improvement, there are still problems. Whereas before all four partitions from the external HD appeared automatically on the Desktop, now I have to run "sudo mount -a" to get the ntfs partitions to appear.
However, only two ntfs parttions actually mont and the third ntfs partition still refuses to mount. I get the following error from "sudo mount -a":
```
mount: mount point media/SCSI0_VOL4 does not exist 
```

However, there certainly IS a folder named SCSI0_VOL4 in /media. So it is not clear why it is considered not to exist.

Can anybody help me figure out what's gone wrong here?

---

### Post by dttk on 2007-03-06
Maybe it the missing / in front of the media

/dev/sda1       /media/SCSI0_VOL1    ntfs defaults,nls=utf8,umask=022   0       0
/dev/sda5       /media/SCSI0_VOL2  ntfs defaults,nls=utf8,umask=022  0       0
/dev/sda7      [COLOR="Red"]** media/SCSI0_VOL4**[/COLOR]  ntfs defaults,nls=utf8,umask=022  0       0

Try it and see.

---

### Post by PaulFXH on 2007-03-06
Your observation is correct.
However, I had already spotted his and noted it in the edit (see top of post).
Thanks anyway
Paul

---

