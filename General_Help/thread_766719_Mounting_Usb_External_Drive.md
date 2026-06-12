---
title: "Mounting Usb External Drive"
date: 2008-04-25
forum: General Help
---

### Post by securitybreach on 2008-04-25
I have been running Ubuntu 8.04 Beta for a couple of weeks with no problem but yesterday I reinstalled the Final release and I am having problems mounting my WD MyBook 500gb external usb harddrive. I get the error when I try to mount it:
```
CANNOT MOUNT VOLUME
Invalid mount option when attempting to mount the volume 'MY BOOK'.
``` I am not for sure if the drive is formatted as ntfs or fat32 but my windows partition (ntfs) on the main harddrive can be mounted easily. BTW the harddrive can be mounted on my laptop which is still running 8.04 beta.


Any ideals?

THanks

---

### Post by Propaghandi on 2008-04-25
> **securitybreach said:**
> Any ideals?

World Peace!

---

### Post by bollix47 on 2008-04-25
You might want to check /etc/fstab to see if it is listed and has the right UUID.

To get a list of disk devices:

```
sudo fdisk -l
```

To get the device info:

```
sudo blkid /dev/sda?
```

/dev/sda? should be changed to the device identified above.

To edit fstab:

```
gksudo gedit /etc/fstab
```

Make any changes or add the device according to the output from blkid above.

---

### Post by securitybreach on 2008-04-25
First of all thanks for the help but I know all of those commands and I have looked through out fstab. Wouldnt HAL take care of this? Also, why would it be in fstab if it is not always connected? I do not have an entry in any other distros and the drive works fine. Since I have multiple flash drives it would not be very efficient to have every device listed in fstab. Besides Slackware, all the other distros I have used (including  Ubuntu 8.04 beta) automatically mount drives without having to touch /etc/fstab using HAL or equivalent. I will compare my Laptops fstab with this machine's fstab to see if I can get it to work. BTW my Laptop also has Ubuntu 8.04 beta, go figure.

THanks

---

### Post by securitybreach on 2008-04-25
Also, ntfs-3g is working correctly. I can mount my windows partition just fine. But no flash drives or external drives will mount. Here are the commands:

```
comhack@Venus:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f800000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375        8806    19535040   83  Linux
/dev/sda3            8807        9171     2931862+  82  Linux swap / Solaris
/dev/sda4            9172       60801   414717975   83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08124c68

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38914   312571192+   7  HPFS/NTFS
```

```
comhack@Venus:~$ sudo blkid /dev/sdb1
/dev/sdb1: UUID="FEFCFEC6FCFE786B" LABEL="MY BOOK" TYPE="ntfs" 
```

Thanks

---

### Post by bollix47 on 2008-04-25
I just tried this on an up-to-date Hardy(fresh install) to see if I had the same problem but it mounted and displayed the file browser as soon as I plugged it in.

You've probably already tried this but just in case, have you unplugged it from the usb port and plugged it back in while the o/s is running?

Fdisk shows it as a 320gb drive but in your OP you said it was 500gb.  Was that just a typo?

Sorry I'm not much help but like I said, on mine it just works the way you would think it's supposed to.

---

### Post by bollix47 on 2008-04-25
Check your /etc/fstab and make sure it doesn't have /dev/sdb1 assigned to a cdrom drive.

[http://ubuntuforums.org/showpost.php?p=4756320&postcount=13](http://ubuntuforums.org/showpost.php?p=4756320&postcount=13)

Another thread with similar problems:

[http://ubuntuforums.org/showthread.php?t=731357&highlight=usb+hard+drive+mount](http://ubuntuforums.org/showthread.php?t=731357&highlight=usb+hard+drive+mount)

---

### Post by securitybreach on 2008-04-25
> **bollix47 said:**
> I just tried this on an up-to-date Hardy(fresh install) to see if I had the same problem but it mounted and displayed the file browser as soon as I plugged it in.

You've probably already tried this but just in case, have you unplugged it from the usb port and plugged it back in while the o/s is running?

Fdisk shows it as a 320gb drive but in your OP you said it was 500gb.  Was that just a typo?

Sorry I'm not much help but like I said, on mine it just works the way you would think it's supposed to.



Thanks for the suggestions and yes it was a type.I looked at fstab again and now it seems that sdb1 was listed as a cdrom but I do not think it was there before. It might have something to do with me leaving it plugged in during a reboot. Anyway its fixed. Thanks everyone

THanks

---

### Post by Endolith on 2008-04-27
I've had the same problem since the Feisty upgrade.  Tried reinstalling HAL, checked fstab and there is no /dev/sdb1 assigned to cdrom drive.

[http://ubuntuforums.org/showthread.php?t=608210](http://ubuntuforums.org/showthread.php?t=608210)

---

