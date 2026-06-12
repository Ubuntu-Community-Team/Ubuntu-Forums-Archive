---
title: "Corrupt NTFS Partition Table"
date: 2008-06-24
forum: General Help
---

### Post by anubis2591 on 2008-06-24
So right now I'm stuck with a corrupt NTFS partition on my 200GB USB backup drive. I think it became corrupt with a bad unmounting on one of my xubuntu systems. Now I'm trying to recover it. I'm running gpart right now but I think it might have hung. Here's the output of gpart.

```
sudo gpart -v /dev/sdc

dev(/dev/sdc) mss(512) chs(24792/255/63)(LBA) #s(398283480) size(194474mb)

* Warning: strange partition table magic 0x0000.
Primary partition(1)
   type: 000(0x00)(unused)
   size: 9mb #s(19776) s(4029743104-4029762879)
   chs:  (0/0/0)-(0/0/0)d (250839/231/17)-(250841/35/10)r
   hex:  00 00 00 00 00 00 00 00 00 00 31 F0 40 4D 00 00

Primary partition(2)
   type: 007(0x07)(OS/2 HPFS, NTFS, QNX or Advanced UNIX) (BOOT)
   size: 194474mb #s(398283417) s(63-398283479)
   chs:  (0/1/1)-(1023/254/63)d (0/1/1)-(24791/254/63)r
   hex:  80 01 01 00 07 FE FF FF 3F 00 00 00 99 52 BD 17

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
   hex:  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
   hex:  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00


Begin scan...

```

It's been stuck like that for two hours. But the drive access light on, on the backup drive. Is it supposed to take that long. And do you have any other suggestions for how to fix this. Oh and here's the output of fdisk:

```
sudo fdisk -l

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd478bc7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2363    18980766   83  Linux
/dev/sda2            2364        2432      554242+   5  Extended
/dev/sda5            2364        2432      554211   82  Linux swap / Solaris

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

```

Thanks for your help.

---

