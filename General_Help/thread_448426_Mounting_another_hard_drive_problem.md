---
title: "Mounting another hard drive problem"
date: 2007-05-19
forum: General Help
---

### Post by TotalRetard on 2007-05-19
So,

I have two hardrives on my computer. The other has Windows XP on it, partitioned in two pieces.
The other one has an installation of Ubuntu 7.04 on it, but I can't seem to mount the other partition from my Windows hard drive.

```
kalle@Elitekone:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276       19456   146038882+   f  W95 Ext'd (LBA)
/dev/sda5            1276       19456   146038851    7  HPFS/NTFS

Disk /dev/sdb: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         743     5968116   83  Linux
/dev/sdb2             744         784      329332+   5  Extended
/dev/sdb5             744         784      329301   82  Linux swap / Solaris

```

Then, when I try to mount the desired partition:
```
kalle@Elitekone:~$ sudo mount -t ntfs /dev/sda5 /mnt/windrive -o "unmask=022"
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

that happens...

Well, I've read enough and searched enough, but can't fix my problem :confused:

Edit:
dmsg | tail prints out:
```
[ 2720.496677] NTFS-fs error (device sda5): parse_options(): Unrecognized mount 
```

---

### Post by TotalRetard on 2007-05-19
Edit: I need to stop asking stupid questions.

Have a nice day.

---

