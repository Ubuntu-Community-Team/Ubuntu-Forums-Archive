---
title: "[SOLVED] KDE startup error"
date: 2008-06-16
forum: General Help
---

### Post by fleisc on 2008-06-16
After KDE starts up a Konqueror Error window appears that says Could not mount device. The reported error was: No such medium.

Everything seems to working fine (usb devices, dvd, etc.) so I'm not sure what could be causing this. Any ideas on how to fix this?

---

### Post by ChameleonDave on 2008-06-16
Please post the output of this (from the terminal):

```

cat /etc/fstab
ls -l /dev/disk/*
sudo fdisk -l

```

---

### Post by fleisc on 2008-06-16
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=88a86b85-6029-4930-939d-371df1b5e5ae /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=26AC1D71AC1D3D2D /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=81f69e11-7813-4384-b076-6789efc0af55 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

$ ls -l /dev/disk/*
/dev/disk/by-id:
total 0
lrwxrwxrwx 1 root root  9 2008-06-16 14:42 ata-ST3320620AS_5QF08V9M -> ../../sda
lrwxrwxrwx 1 root root 10 2008-06-16 14:42 ata-ST3320620AS_5QF08V9M-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-06-16 14:42 ata-ST3320620AS_5QF08V9M-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-06-16 14:42 ata-ST3320620AS_5QF08V9M-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-06-16 14:42 ata-ST3320620AS_5QF08V9M-part5 -> ../../sda5
lrwxrwxrwx 1 root root  9 2008-06-16 14:42 scsi-1ATA_ST3320620AS_5QF08V9M -> ../../sda
lrwxrwxrwx 1 root root 10 2008-06-16 14:42 scsi-1ATA_ST3320620AS_5QF08V9M-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-06-16 14:42 scsi-1ATA_ST3320620AS_5QF08V9M-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-06-16 14:42 scsi-1ATA_ST3320620AS_5QF08V9M-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-06-16 14:42 scsi-1ATA_ST3320620AS_5QF08V9M-part5 -> ../../sda5

/dev/disk/by-path:
total 0
lrwxrwxrwx 1 root root 10 2008-06-16 14:42 pci-0000:00:04.0-scsi-0:0:0:0 -> ../../scd0
lrwxrwxrwx 1 root root  9 2008-06-16 14:42 pci-0000:00:05.0-scsi-0:0:0:0 -> ../../sda
lrwxrwxrwx 1 root root 10 2008-06-16 14:42 pci-0000:00:05.0-scsi-0:0:0:0-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-06-16 14:42 pci-0000:00:05.0-scsi-0:0:0:0-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-06-16 14:42 pci-0000:00:05.0-scsi-0:0:0:0-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-06-16 14:42 pci-0000:00:05.0-scsi-0:0:0:0-part5 -> ../../sda5

/dev/disk/by-uuid:
total 0
lrwxrwxrwx 1 root root 10 2008-06-16 14:42 26AC1D71AC1D3D2D -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-06-16 14:42 81f69e11-7813-4384-b076-6789efc0af55 -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-06-16 14:42 88a86b85-6029-4930-939d-371df1b5e5ae -> ../../sda2
$ fdisk -l

there was no output from the last command

---

### Post by ChameleonDave on 2008-06-16
> **fleisc said:**
> 

there was no output from the last command

Sorry, that one needed to be run as root.

---

### Post by fleisc on 2008-06-16
Thanks, here it is:

$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd94fd94

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4033    32395041    7  HPFS/NTFS
/dev/sda2            4034       38740   278783977+  83  Linux
/dev/sda3           38741       38913     1389622+   5  Extended
/dev/sda5           38741       38913     1389591   82  Linux swap / Solaris

---

### Post by ChameleonDave on 2008-06-16
> **fleisc said:**
> 
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


Seems fine.  The only thing that looks strange to me is the line that handles your optical drive.  Mine says "scd0" rather than "hda".  Yours could be perfectly correct though.

Perhaps you could comment out that line in your fstab (by putting a # at the start of the line) and see if the error persists.

---

### Post by fleisc on 2008-06-16
Yeah, same thing happens even when I comment out that line.

---

### Post by ChameleonDave on 2008-06-17
OK, so this happens when KDE starts, and not at any other time?

And we're talking about KDE 3, not 4, right?

Post the output of 

```

ls -l ~/.kde/Autostart/

```

---

### Post by fleisc on 2008-06-17
This is KDE 3.5.9 on Kubuntu 8.04 and it only happens once right after login.

$ls -l ~/.kde/Autostart/
total 0

---

### Post by Zorael on 2008-06-17
If you (temporarily) create a new user, does this happen for him/her/it as well?

Conjecture: Some Konqueror setting - perhaps a bookmark, or the Konqueror home folder - being set to an invalid directory?

---

### Post by fleisc on 2008-06-17
I created a new user and I did not see that same error. So it must be a setting some where. I think it's trying to mount my external USB hard drive, because if I turn on the drive before logging in the error does not show up. Is there a setting I could change so that KDE doesn't try to mount the external drive when I log in if the external drive is off?

---

### Post by Zorael on 2008-06-17
Hum. Well, you could try to wipe Konqueror's settings.
```
$ killall konqueror
$ cd ~/.kde/share/apps
$ mv konqueror konqueror.backup
$ konqueror &
```
That might just do it.

---

### Post by fleisc on 2008-06-17
That worked! I don't see the the error anymore. Thanks for your help I was getting pretty tired of seeing that error every day.

---

