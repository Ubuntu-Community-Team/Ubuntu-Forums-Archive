---
title: "How do I mount fakeraid?"
date: 2007-10-20
forum: General Help
---

### Post by rudlavibizon on 2007-10-20
Hi, i have a jmicron raid0 formated as ntfs in Windows. I installed dmraid and it successfully detected it (i can see it in /dev/mapper) but i'm unable to mount it.

```
 sudo mount -t ntfs-3g /dev/mapper/jmicron_JRAID\ \ \ \ \ \ \ \ \ \ \  /media/raid 
NTFS signature is missing.
Failed to mount '/dev/mapper/jmicron_JRAID           ': Invalid argument
The device '/dev/mapper/jmicron_JRAID           ' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```

I tried reading [this how-to]("https://help.ubuntu.com/community/FakeRaidHowto") but it's more like for installing a system on it rather than just mounting it as storage for both ubuntu and windows.

Here is my fdisk -l:

```
rudlavibizon@rudlavibizon-linux:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13170f05

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       77819   625081086   42  SFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10a710a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sdc2            6375       24321   144159277+   f  W95 Ext'd (LBA)
/dev/sdc5            6375       24321   144159246    7  HPFS/NTFS

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6154a347

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        2432    19535008+  83  Linux
/dev/sdd2            2433        9484    56645190    5  Extended
/dev/sdd5            2433        8511    48829536   83  Linux
/dev/sdd6            8512        9484     7815591   82  Linux swap / Solaris

Disk /dev/dm-0: 640.0 GB, 640084344832 bytes
255 heads, 63 sectors/track, 77819 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13170f05

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1   *           1       77819   625081086   42  SFS

```

---

### Post by fjgaude on 2007-10-20
What does a sudo dmraid -r show?

I use to mount like this:

```
sudo mount -t ntfs-3g /dev/mapper/JMiicron_abahabcfjg /media/raid
```

The "abahabcfjg" you get from what you find from -r above.

Of course you have to have ntfs-3g installed, using apt-get or Synaptic.

---

### Post by rudlavibizon on 2007-10-21
here is dmraid -r:

```
rudlavibizon@rudlavibizon-linux:~$ sudo dmraid -r
/dev/sdc: jmicron, "jmicron_JRAID           ", stripe, ok, 625082368 sectors, data@ 0
/dev/sdd: jmicron, "jmicron_JRAID           ", stripe, ok, 625082368 sectors, data@ 0

```

---

### Post by fjgaude on 2007-10-21
I don't know what to make of all the blanks, spaces after the _JRAID. What does dmraid -tay show?

---

### Post by rudlavibizon on 2007-10-21
Here it is. Meanwhile i tried reformating in XP but same happens no matter:

```
rudlavibizon@rudlavibizon-linux:~$ sudo dmraid -tay
[sudo] password for rudlavibizon:
jmicron_JRAID           : 0 1250164736 striped 2 256 /dev/sda 0 /dev/sdb 0
jmicron_JRAID           5: 0 1250146107 linear /dev/mapper/jmicron_JRAID            16128

```

---

### Post by rudlavibizon on 2007-10-21
Hm, i just tried formating it as ext3 and it mounted ok. But I need it for both XP and Ubuntu so it has to be ntfs. :(

Oh, and I just deleted the blanks...

---

### Post by fjgaude on 2007-10-21
I guess I don't know what to suggest next. Maybe there are others here that have come across what you are doing. Good luck.

---

### Post by rudlavibizon on 2007-10-21
OK ,thanks anyway, I'll post the solution if i find it.

---

