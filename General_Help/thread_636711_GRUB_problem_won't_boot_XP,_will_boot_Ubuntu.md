---
title: "GRUB problem: won't boot XP, will boot Ubuntu"
date: 2007-12-10
forum: General Help
---

### Post by cold_fu5ion on 2007-12-10
Hi,
I just installed XP onto a new hard drive after I had ubuntu already installed on a separate drive. I did the usual grub restore using the live cd to get ubuntu back, but grub didn't pick up windows. I think this is because I added a drive. I updated device.map and reinstalled grub using this .map file and added xp to my menu.lst. 

When I try to boot what I think is the xp partition it just sits ther saying "Starting up..." and never gets past that, I've also tried editing grub to try everything from hd0,0 to hd2,2. I tried the super grub cd and it works to boot windows using is automatic windows boot option. Is there anyway to tell what parameters it is using to boot windows? 

I use windows so rarely that going through super grub wouldn't be too bad, although I would like to know what I'm doing wrong. Here's my menu.lst, device.map and fdisk -l output. XP is on the IDE drive hdd, Ubuntu work fine using grubs current config.....

```
Disk /dev/hdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe3b3e3b3

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e4abf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *        7706       38913   250678260    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6374    51199123+  83  Linux
/dev/sdb2   *        6375        6629     2048287+  82  Linux swap / Solaris
/dev/sdb3            6630       38913   259321230    7  HPFS/NTFS

```


```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4a757c22-ff81-458f-99dc-cef00037290a ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet


title		Windows XP
root		(hd2,1)
makeactive
chainloader	+1
```

```

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/hdd
```

Any help would be great. Thanks :)

---

### Post by Portable_Jim on 2007-12-10
You might want to add ```
savedefault
``` to the middle of the Windows option.
This is my Windows lines:
```
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

---

### Post by cold_fu5ion on 2007-12-10
I just tried that out and I get the same result. I think I should be trying to boot XP from hd2,0 but this gives me "partition does not exist" or words to that effect, while hd2,1 gives me the "starting up...." freeze.

---

### Post by Portable_Jim on 2007-12-10
Sorry, however I am not sure what the problem is. Maybe someone else will know. See if you can find out something using Google.

---

### Post by mikewhatever on 2007-12-10
Grub should see /dev/hdd1 as hd2,0, since it counts partitions starting from zero. Try changing the entry for Windows accordingly, in other words, to 
title		Windows XP
root		(hd2,0)
makeactive
chainloader	+1
If it does not work, look here --> [http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk)

---

### Post by IeU on 2007-12-10
Hi,

i do also have a problem,

Ubuntu is booting ok, but XP does not.

What is wrong ?

Ubuntu is on sdb, xp on sda.

```
felipe@felipe-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38ef38ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbed35df

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          64      514048+  83  Linux
/dev/sdb2              65        1339    10241437+  83  Linux
/dev/sdb3            1340        1466     1020127+  82  Linux swap / Solaris
/dev/sdb4            1467       18241   134745187+  83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x909e622d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60802   488384512    7  HPFS/NTFS

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ffc810

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       38912   312560608+   7  HPFS/NTFS

Disk /dev/sde: 1014 MB, 1014497280 bytes
65 heads, 32 sectors/track, 952 cylinders
Units = cylinders of 2080 * 512 = 1064960 bytes
Disk identifier: 0x32b73a58

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1         953      990704    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(967, 64, 32) logical=(952, 39, 32)
```
```

felipe@felipe-desktop:~$ sudo cat /boot/grub/device.map
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc
(hd3)   /dev/sdd
(hd4)   /dev/sde

```

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=d64a0f5d-0b3e-44bb-b114-868f5a9f0935 ro quiet splash
initrd		/initrd.img-2.6.22-14-generic
quiet

title           Microsoft Windows XP Professional Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=d64a0f5d-0b3e-44bb-b114-868f5a9f0935 ro single
initrd		/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet
```

another thing i dont understand,

if Ubuntu is on "**(hd1)   /dev/sdb**" and XP on "**(hd0)   /dev/sda**"

how the hell is ubuntu booting ok when on Grub/menu.lst is calling ubuntu on "**root		(hd0,0)**", should not be "**root		(hd1,0)**" ?

thanks for the help.

---

### Post by IeU on 2007-12-10
bump, help and info needed :)

thanks

---

### Post by mikewhatever on 2007-12-10
IeU, bumping your request every hour is not nice. The windows entry should look something like this:
title           Microsoft Windows XP Professional Edition
root            (hdx,0)
savedefault
makeactive
chainloader     +1

hdx should not be hd0, since that's where Ubuntu is. Try 1, or 2.

---

### Post by froy02 on 2007-12-11
Linux/ubuntu  counts from 0, so the output from fdisk like /dev/hd1 is should be entered in menu.lst as (hd0).
Also we need to know which hard drive is set to boot first in your bios. Is it the IDE or the Sata?
Anyway here's the website that will help you reinstall grub properly.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Hope it helps you.  I used it it when I had to install XP on another hard drive and it worked perfectly.  You need a live cd.

---

### Post by cold_fu5ion on 2007-12-11
Hi again, thanks for the replies.

The IDE drive that windows is on is set to boot third in bios. I changed my menu.lst according to the link suggested by mike to:

```

title		Windows XP
root		(hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader	+1
```

I still get "error 22: no such partition" when i try to boot (hd2,0). hd2,1 still says "starting up..." and freezes even though there is no partition there. Very odd.

---

### Post by IeU on 2007-12-11
> **froy02 said:**
> Linux/ubuntu  counts from 0, so the output from fdisk like /dev/hd1 is should be entered in menu.lst as (hd0).
Also we need to know which hard drive is set to boot first in your bios. Is it the IDE or the Sata?
Anyway here's the website that will help you reinstall grub properly.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Hope it helps you.  I used it it when I had to install XP on another hard drive and it worked perfectly.  You need a live cd.

sdb ( linux ) is set as first in boot
sda ( windows ) as second

so i should set windows, Hd(1,x)

how can i tell what to enter in x ?
[B]
edit[/B]
> I still get "error 22: no such partition" when i try to boot (hd2,0). hd2,1 still says "starting up..." and freezes even though there is no partition there. Very odd.

same here, ubuntu is fine,

but windows (Hd(1,0)) does the same thing . . . "starting up..." and stays there.
i tryed also Hd(1,1), gave me an error, if i am not mistaken ( no partition ).

---

### Post by IeU on 2007-12-11
bump

please, i really need to boot my xp :/

---

### Post by IeU on 2007-12-11
help please.

---

