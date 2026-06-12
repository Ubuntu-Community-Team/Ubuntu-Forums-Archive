---
title: "LUKS LVM turned unallocated disk space"
date: 2017-04-10
forum: General Help
---

### Post by desfritz on 2017-04-10
Hello forum,

 I need some help with an encrypted LVM containing my Linux installation, that turned into unallocated disk space.
 
 2 Harddisks
 - 180GB  (/dev/sda = A)
 - 1TB  (/dev/sdb = B)
  
 ```
/dev/sda1 = (old winXP OEM)
 /dev/sda2 = (Linux test installation)
 /dev/sda3 = unencrypted /boot for Linux
 /dev/sda4 = extented
 /dev/sda6 = encrypted LVM with installed linux
 (/dev/sda7 = games for Win)
 /dev/sda5 = shared partition for Win/Linux

/dev/sdb1 = empty 20GB
/dev/sdb2 = empty 20GB
...some unimportant other ones...

(the order is increasing blocks on harddisk, so /dev/sda5 is on the 'end' of the disk)
 
```

There were two empty primary partitions on B with 20GB each and some other. I deleted them both with gparted and created one 40GB partition to install Windows 7 for testing some 64bit things.
I restarted the system and encrypted Linux from LVM was running fine. So I booted from Win7-DVD, formated the 40GB partiton (new /dev/sdb1) and installed Win7.
I realized, that the 50GB partition was gone (GAMES). WinXP started, so I did not format /dev/sda1 instead.
I thought the GAMES were gone, because for some reason, they might have been split up on /dev/sdb1 and/dev/sdb2 with some ntfs folder mounting hack or something, but that is fine. Nothing lost, don't need them.
  
Rebooted with LiveDVD to rewrite GRUB and realized, that there was just a huge unallocated disk space on A.
But why was the encrypted LVM unallocated disk space? Does not matter, I need it back somehow...
  
I checked with fdisk and created a partition table entry as linux partition  typ 83 as /dev/sda6
I hexdumped   "hexdump -C -n 512 /dev/sda6/"   but received only zeros. 
But the later sectors contained something. garbage, encrypted, but I was sure there was nothing wiped out/zeroed etc.
 
I had backups/printouts from fdisk/fstab etc. so I could see the starting and ending sectors, but I used all the space first. (old data...)
I restored the LUKS header for /dev/sda6 and opened it. Password fine, the right header.
But I could not mount it directly, as this LUKS contains a LVM. So I tried to vgscan etc. but nothing was found.
 
I erased Win7 and installed Linux on /dev/sdb1 so I could go withoud liveDVD, slept one night, to calm down and thought about the GAMES-partition.
It could not be on /dev/sdb1 & 2, and was sure there was no ntfs-hack involved. THAT would have went into my handbook.
So I read through my config printouts and realized, that the unallocated disk space on /dev/sda had to be two partitions, not only the encrypted LVM. 
I used old data first...great.
 
 ```
/dev/sda6 = encrypted LVM with installed linux
 /dev/sda7 = games for Win
```
 
 As I had the sectors written on some page in my handbook, I deleted the huge /dev/sda6  from  yesterday  with fdisk an created:

 ```
/dev/sda7 with 15962368 to 567513855 as type 7
```

 Voila: It was detected as label=games.local and could be mounted. All files there.
 
 So right now I still have a fool's hope, that maybe the encrypted LVM could still be read somehow.
 
My handbook tells me:
 ```
/dev/sda6 61966336 to 159621119 total 48827392, 83 linux LVM LUKS (about 45GB)
```
 
 I restored LUKS header back to /dev/sda6 which should be the same address as yesterday, because the starting sectors should be the same.
 
 Here's something that bothers me a bit:
 My written notes tell me the starting sector 61966336
 But fdisk tells me, that the first sector can only be 61968384
 
```
 Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *           63  30719999  30719937  14,7G  7 HPFS/NTFS/exFAT
/dev/sda2        30720000  61439999  30720000  14,7G 83 Linux
/dev/sda3        61440000  61964287    524288   256M 83 Linux
/dev/sda4        61966334 312576704 250610371 119,5G  f W95 Ext'd (LBA)
/dev/sda5       267514443 312576704  45062262  21,5G  7 HPFS/NTFS/exFAT
+/dev/sda6        61968384 159621119  97652736  46,6G 83 Linux
/dev/sda7       159623168 267513855 107890688  51,5G  7 HPFS/NTFS/exFAT
```

I have found a printout with the table above, but the starting sector for /dev/sda6 is 61966336 in that printout! Not handwritten, printed(!).
The last printed out fdisk with all partitions from 1 to 7. 

I am right now a bit lost and need some help, what to do next and do not really know, how to handle/mount/access/check LVM from command line.
And I think it is a bad time for testing right now, so I would rely on your help instead of trying things out on my own.
Maybe restoring the LUKS header back to wrong sectors allready killed it, but I just created the partition within the range that fdisk allowed...
(and hexdump only returned zeros...)


Regards, Fritz

---

### Post by desfritz on 2017-04-10
UPDATE:
Did a search over the harddisk for 'LUKS'

```
dd if=/dev/sda bs=512 count=66000000 skip=63 | hexdump -C | grep 'LUKS'    
[...]
763000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
7631f8200  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
[...]

```

One is located here: 61968384
```
dd if=/dev/sda bs=512 count=1 skip=61968384 | hexdump -C
00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  78 74 73 2d 70 6c 61 69  |........xts-plai|
00000030  6e 36 34 00 00 00 00 00  00 00 00 00 00 00 00 00  |n64.............|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
...

```
This is the one I restored from LUKS header backup image.
Is it hexaddress '763000000' or '7631f8200' from the long scan? Math?
Maybe there is another header, so the assumed starting position was wrong?

---

