---
title: "having Trouble With USB hard Drive"
date: 2008-04-14
forum: General Help
---

### Post by Number1Dad on 2008-04-14
I am trying to make the switch to Linux, but I am having a lot of trouble with mounting a few hard drives. This particular hard drive is an IDE drive that is in one of those USB external cases. It was formatted in NTFS using the Windows drive manager. When I try to open it, I get an error message that reads "Unable to mount location, can't mount file." I tried enabling it using ntfs-config to no avail. The results of sudo fdisk -l:

[PHP]Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08b75bf7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS
[/PHP]

I am really enjoying my experience so far and I don't want this to spoil it. Thank you in advance!

---

### Post by greenstar on 2008-04-14
OK, plug it up and then give me the output from:
```
cat /etc/mtab
```

Greenstar

---

### Post by Number1Dad on 2008-04-14
[PHP]/dev/sda7 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-12-generic/volatile tmpfs rw 0 0
/dev/sda1 /media/sda1 vfat rw,utf8,umask=007,gid=46 0 0
/dev/sda5 /media/sda5 vfat rw,utf8,umask=007,gid=46 0 0
securityfs /sys/kernel/security securityfs rw 0 0
/dev/sda2 /media/sda2 fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
[/PHP]

---

### Post by Number1Dad on 2008-04-14
I solved this myself.

---

### Post by greenstar on 2008-04-14
Care to share your solution?

---

### Post by photopath on 2008-04-16
I'm having the same problem with a compressed USB drive, formatted with NTFS under XP Pro.

Is there an easy fix to this?

:confused:

---

### Post by bigfoot.blade on 2008-05-01
Can you share the solution pls? I've the same problem!

---

### Post by greenstar on 2008-05-01
> **Number1Dad said:**
> I am really enjoying my experience so far and I don't want this to spoil it. Thank you in advance!

> **Number1Dad said:**
> I solved this myself.

Here we have a great example of selfishness. This person thinks it's acceptable to bother others with his problems and take advantage of their time and knowledge, yet can't be bothered to contribute anything himself. Would it have been so hard to contribute the solution that he found? It's this kind of person who is "dead weight" to a community-based project such as Ubuntu. There are at least three people who might've benefited from this solution.

---

