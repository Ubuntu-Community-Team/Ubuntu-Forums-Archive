---
title: "mtab missing, boot files missing"
date: 2008-02-29
forum: General Help
---

### Post by iscreamkid on 2008-02-29
My boot folder is totally empty except for the two dot files thus I no longer have a grub folder.
I can't use my CD or external HDD drive because the mtabs file is missing.


I need to get the mtab feature working so I can use my CD but I am not sure how to go about it.
I would like to rebuild GRUB but I don’t think I can without the CD to run SuperGRUB

When I tried to replace the mtab file with sudo I received an IO/error message.

I have a live CD but it will only run by booting it. I could download an ISO or I could wipe and reload from scratch losing a weeks work.

I have a DELL Inspioion 530 that came preloaded with Ubuntu, now up graded to Gutsy 7.10.
I do not know what special tweaking DELL used in their installation. 

I am relatively new to the Linux environment.

---

### Post by pointone on 2008-02-29
What caused this problem to occur? Just upgrading to 7.10, or were you messing around with other settings?

Post the output of "cat /etc/fsatb" and "sudo fdisk -l", please.

---

### Post by iscreamkid on 2008-02-29
The only change I am aware of was being fed upgrades for nearly every language on the earth and I installed Qt 3 with its associated documentation. 

Everything else I have been doing the last couple of weeks is non destructive things like browsing, word processing and adding to my local wiki.

---

### Post by iscreamkid on 2008-02-29
Oops, I missed second line sorry:

cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=804ad7fd-541b-45cf-889e-4da7b7a9314e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=60ffe8b6-dadb-4e39-b794-3b646654cdfc none            swap    sw              0       0
# 080104  B/U file made. Added unhide to cdrom0 so it can be used by WINE.
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,unhide     0       0
UUID=0b36649b-6957-42ea-b7c2-adb9c6b6fe0e  /boot ext3 defaults 0 0
koder@dell:/$       

sudo fdisk -l
[sudo] password for koder:

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2               7         268     2104515    b  W95 FAT32
/dev/sda3   *         269         293      200812+  83  Linux
/dev/sda4             294       30394   241786282+   f  W95 Ext'd (LBA)
/dev/sda5             294         455     1301233+  82  Linux swap / Solaris
/dev/sda6             456       30394   240484986   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb762b18d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30400   244187968+  83  Linux
/dev/sdb2           30401       60801   244196032+  83  Linux

The second gadget is an external HDD that I would like to use to back up data.

---

### Post by pointone on 2008-02-29
It's possbile an update may have changed the UUID of your boot partition. Run "sudo blkid".

---

### Post by iscreamkid on 2008-02-29
Thanks for the response

sudo blkid
[sudo] password for koder:
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-0A14" TYPE="vfat"
/dev/sda5: TYPE="swap" UUID="60ffe8b6-dadb-4e39-b794-3b646654cdfc"
/dev/sda2: LABEL="OS" UUID="A85B-3924" TYPE="vfat"
/dev/sda3: LABEL="os_part" UUID="0b36649b-6957-42ea-b7c2-adb9c6b6fe0e" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda6: LABEL="os_part" UUID="804ad7fd-541b-45cf-889e-4da7b7a9314e" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdb1: LABEL="/home2" UUID="77653c3b-ff04-4fc4-a09d-0fa0881cf6de" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdb2: LABEL="/bu" UUID="349fd6e2-f89c-40ff-9b4d-143b122dd238" SEC_TYPE="ext2" TYPE="ext3"

---

### Post by pointone on 2008-02-29
Hmmm... The UUID's match up fine, so that's not it.

What happens when you try to run "sudo mount /boot"?

---

### Post by iscreamkid on 2008-02-29
Thanks for the response.

I am away from my machine for the night, I will try  your test first thing tomorrow morning.

I can browse to the/boot folder using either konqueror or terminal so I am pretty sure it is mounted. 
The only files I see are the dot and dot dot files in /boot. ( . and .. ).
When I booted with the Ubuntu live CD it showed a partition on my system labeled boot.


In the /etc folder I have a multitude of files including fstab, but not mtab (if I have correct spelling) When I plug the external hard drive into the USB port I get an error message (from faulty memory) saying I have an I/O error with the mtab files and they can't mount the drive.

If I can mount the drive I will back up data and reload whole OS and start over if there is no better way of recovering. If I could get the CD to run I could run Super GRUB per one of the Forum's suggestions and reinstall the GRUB files although that would not put the correct kernel in.

---

### Post by iscreamkid on 2008-03-01
koder@dell:~$ sudo mount /boot
[sudo] password for koder:
mount: can't open /etc/mtab for writing: Input/output error
koder@dell:~$

I tried to make a file so it would have someplace to write to and it went like this:

koder@dell:~$ sudo touch /etc/mtab
touch: cannot touch `/etc/mtab': Input/output error

Using sudo I can create and delete files in /etc with other names

      sudo finger testtrash

gave me the file testtrash

---

### Post by pointone on 2008-03-01
Sounds like your root partition may have some problems. 

```
sudo touch /forcefsck
```

... and reboot to run a filesystem check.

---

### Post by iscreamkid on 2008-03-01
pointone,

Thank you for the code for manually checking the file system.
I have been wondering how to do that.

I became impatient, wiped the drive and reloaded the OS which resolved the issue.

Again thanks for your responses.

A bag of 
:popcorn:

and a cup of coffeee to go with your chocolate chip cookies.

---

