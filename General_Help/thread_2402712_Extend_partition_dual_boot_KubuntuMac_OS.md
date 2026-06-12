---
title: "Extend partition dual boot Kubuntu/Mac OS"
date: 2018-10-03
forum: General Help
---

### Post by funeoz on 2018-10-03
I would like to extend my Ubuntu partition because the more I use it, the more it takes space. My other partition is a Mac OS one.
I want to do it without corrupting my files.
 And should I use GParted or KDE Partition Manager?

---

### Post by TheFu on 2018-10-03
The answer is "it depends".  Without seeing how the partitions are setup, it is impossible to provide a sane answer.
```

sudo fdisk -l
df -Th
```
would be the minimal information necessary. When posting that output, please include the exact commands and output - no need for any "loop" devices.  Also, please use "code tags" as I've done.  Things line up that way.  No images, please.

---

### Post by funeoz on 2018-10-04
It is in French but I think you can read it without any problems.

```


[FONT=monospace][COLOR=#000000]**Disque /dev/sda : 298,1 GiB, 320072933376 octets, 625142448 secteurs**[/COLOR]
Unités : secteur de 1 × 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Type d'étiquette de disque : gpt
Identifiant de disque : 00001180-0DA4-0000-511D-0000AE150000

[COLOR=#000000]**Périphérique**[/COLOR][COLOR=#000000]**     Start       End  **[/COLOR][COLOR=#000000]**Sectors**[/COLOR][COLOR=#000000] **  Size **[/COLOR][COLOR=#000000]**Type**[/COLOR]
/dev/sda1           40    409639    409600   200M Système EFI
/dev/sda2       409640 425173655 424764016 202,6G Stockage d'Apple Core
/dev/sda3    425173656 426443191   1269536 619,9M Amorçage Apple
/dev/sda4    426444800 434255871   7811072   3,7G Partition d'échange Linux
/dev/sda5    434255872 625139711 190883840    91G Système de fichiers Linux
[/FONT]
```

> octets means > bytes


```
[FONT=monospace][COLOR=#000000]df -Th[/COLOR]
File system      Type        Size   Used   Free Uti% Mount on 
udev             devtmpfs   1,9G       0  1,9G   0% /dev
tmpfs            tmpfs      386M    1,7M  385M   1% /run
/dev/sda5        ext4        90G     32G   54G  37% /
tmpfs            tmpfs      1,9G     18M  1,9G   1% /dev/shm
tmpfs            tmpfs      5,0M    4,0K  5,0M   1% /run/lock
/dev/sda1        vfat       197M     24M  174M  12% /boot/efi
tmpfs            tmpfs      386M     28K  386M   1% /run/user/1000
[/FONT]
```

---

### Post by TheFu on 2018-10-04
All the "loop" stanzas are just clutter. Feel free to remove them to make it less scary for people wanting to help.
I'll take a look ...

<update>

There are some things that I would do differently. It doesn't look like you can extend the ext4 partition, because the disk is already fully allocated.  You have 2 choices (in the realm of simple answers).

a) shrink the Apple partition(s) some way, remove the swap partition, shift the ext4 partition "left" to use the space that was freed from the Apple partition, then recreate a swap partition all the way to the "right" that is the same size as currently used.
or
b) get another HDD, hook it up internally via either SATA or eSATA connections and migrate data over.

There are other options which would try to fix some poor partitioning things that might not seem important now, but will be if you use more and more Linux.  For example, the OS partition should be 25G or smaller.  Mixing the OS and packages installed with "data" is an anti-pattern.  If you keep /home on a separate partition from where the OS is installed, there are many options for upgrades.  It also helps greatly with backups and cloning a system if the OS and data are separated.

BTW, doing any of these things will likely leave you with a system that cannot boot, until you fix the grub setup and fstab.

---

### Post by TheFu on 2018-10-04
BTW, the / partition for linux has 54G free, so you've used less than 50% at this point.  If you want to create a separate /home/ partition, now would be the time before / gets too full.  You can do this with very little risk to data since there is plenty of free space.

Regardless, what ever you do, please make a 100% know-you-can restore everything backup.  People not good with partitioning tend to accidentally wipe things.

---

### Post by funeoz on 2018-10-06
Why should I delete my swap partition then recreate it?

---

### Post by funeoz on 2018-10-06
But I think I don't need to separe my /home partition and my OS one because I don't need to do some cloning or backups. And also I don't use GRUB anymore. I use Refind to manage systems boot.

---

### Post by funeoz on 2018-10-08
Up

---

