---
title: "fstab sda4 grub problem"
date: 2008-01-01
forum: General Help
---

### Post by gh0st3n on 2008-01-01
Hello all.

I used to be a debian user and I used it in harmony with windows xp.
Windows is located at sda4, and I removed debian using the ubuntu live cd and then installed ubuntu. I'm quite pleased with ubuntu, but now it no longer loads my windows! It's still there though, because i can see it in gparted. However, I can't get my sftab configured right anymore. Here's what I have

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda4	/windows	ntfs	nls=utf8,umask=0222	0	0
```

Is this right? Windows is located in my grub, but it doesn't want to boot. Maybe I did something horribly wrong? Anybody know what I might have done wrong? :(

---

### Post by gh0st3n on 2008-01-01
also, this confused me

```
root@hax:/home/nathan# mount /dev/sda4
mount: wrong fs type, bad option, bad superblock on /dev/sda4,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by taurus on 2008-01-01
Can you post

```
sudo fdisk -l
```

---

### Post by gh0st3n on 2008-01-01
this is fdisk -l


```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8707    69938946   83  Linux
/dev/sda2            8708        9079     2988090    5  Extended
/dev/sda4   *        9080       19457    83361285    7  HPFS/NTFS
/dev/sda5            8708        9079     2988058+  82  Linux swap / Solaris

```

---

### Post by taurus on 2008-01-01
What happens when you run this from a terminal?

```
sudo mount -t ntfs /dev/sda4 /windows
```

---

### Post by gh0st3n on 2008-01-01
this looks bad..


```
mount: wrong fs type, bad option, bad superblock on /dev/sda4,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by taurus on 2008-01-01
How did you remove debian from the LiveCD exactly?  Did you just format the partitions or did you delete the partition and then recreated them?

What does gparted say about /dev/sda4?  If you don't have gparted on your machine, System -> Administration, you can install it either from synaptic or terminal.

```
sudo apt-get update
sudo apt-get install gparted
```

---

### Post by jjross on 2008-01-01
I always thought windows needed to be installed on the first partition.
Has that changed?

---

### Post by gh0st3n on 2008-01-01
I simply deleted the partitions.

(i know i have yet to configure my video stuff)
[screenie of gparted]("http://img244.imageshack.us/img244/3879/screenshotei5.png")

---

### Post by gh0st3n on 2008-01-01
never mind.. i just lost all the data anyway because of my dumbness.

---

