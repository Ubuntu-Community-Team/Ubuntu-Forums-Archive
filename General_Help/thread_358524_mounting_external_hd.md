---
title: "mounting external hd"
date: 2007-02-10
forum: General Help
---

### Post by catscape on 2007-02-10
First let me say that I've been searching for an answer for several days now, and so far all the posts that I've seen on the subject have talked about formatting the external as fat32 so that it can easily be accessed by other systems.

Here's what I'm working with: 200gb Maxtor in an external case, usb 2.0, and Ubuntu 6.10

The hard drive used to run Fedora, and held about 30gb worth of irreplaceable data. The mbr got corrupted and would not boot. I then replaced that drive with a smaller spare drive and installed Ubuntu (great decision, btw). 

Plugging in the external usb drive makes it /dev/sda, but it will not mount. 

output from various commands:

fdisk -l

> Disk /dev/sda: 203.9 GB, 203928108544 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   83  Linux
/dev/sda2              14       24792   199037317+  8e  Linux LVM

sudo mount /dev/sda /home/greg/temp -t ext3

> mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg | tail
> 
[17179733.420000] sda: Mode Sense: 03 00 00 00
[17179733.420000] sda: assuming drive cache: write through
[17179733.420000] SCSI device sda: 398297087 512-byte hdwr sectors (203928 MB)
[17179733.420000] sda: Write Protect is off
[17179733.420000] sda: Mode Sense: 03 00 00 00
[17179733.420000] sda: assuming drive cache: write through
[17179733.420000]  sda: sda1 sda2
[17179733.444000] sd 1:0:0:0: Attached scsi disk sda
[17179733.444000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[17181549.440000] VFS: Can't find ext3 filesystem on dev sda.

Not having any success, and like I said, reformatting the disk is out of the question.

Does anyone have any great ideas that will allow me to save this data?

Thanks in advance.

---

### Post by gradedcheese on 2007-02-10
it's /dev/sda1 (or 2), not just /dev/sda

sudo mount -t ext3 /dev/sda2 /home/greg/temp

also note the order of parameters...

---

### Post by catscape on 2007-02-10
> **gradedcheese said:**
> it's /dev/sda1 (or 2), not just /dev/sda

sudo mount -t ext3 /dev/sda2 /home/greg/temp

also note the order of parameters...

I get the same error message as before.
> 
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by gradedcheese on 2007-02-10
Really?  fdisk shows that there's an ext (maybe ext2 rather than 3) FS on it.  Though this doesn't look good:

```
[17181549.440000] VFS: Can't find ext3 filesystem on dev sda.
```

try allowing mount to guess:

sudo mount /dev/sdb2 /home/greg/temp

also, I wouldn't mount into the home directory:

sudo mkdir -p /mnt/extdrive
sudo mount /dev/sdb2 /mnt/extdrive

---

### Post by catscape on 2007-02-10
```
mount: special device /dev/sdb2 does not exist
```

```
root@greg-desktop:/home/greg# mkdir -p /mnt/extdrive
root@greg-desktop:/home/greg# mount /dev/sdb2 /mnt/extdrive
mount: special device /dev/sdb2 does not exist
```

Same results for ext2.  Not looking good.

---

### Post by catscape on 2007-02-10
gradedcheese, thanks for the quick replies, but I've been at this all evening and need some sleep. I'll check in tomorrow morning.

Thanks very much.


edit to add:  I have more information on other things I've tried, but I am too tired to get very deep into it right now.  In a nutshell, I've run TestDisk 6.5, which showed me that the file system is there (but re-writing the mbr didn't help). And running linux rescue after booting from cd showed me that all my files are indeed on the disk. It's just a matter of getting them on a different disk, or maybe networking them somewhere.

---

### Post by catscape on 2007-02-12
bump....

The problem drive is LVM, which apparently is not mountable by Ubuntu. When running linux rescue off the Fedora disk, I can see the files I need, but have no way to copy them anywhere.

Unless anyone can offer a better idea, I think I will try to build a new Fedora box and mount the drive there, then copy to a network drive.

---

