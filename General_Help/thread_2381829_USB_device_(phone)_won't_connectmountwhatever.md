---
title: "USB device (phone) won't connect/mount/whatever"
date: 2018-01-05
forum: General Help
---

### Post by Kris_M on 2018-01-05
17.10 and part way in to 18.04, though I believe this was going on since 17.04 or maybe even earlier. Used to work. I started this build with 16.04 and have updated since.
When I am in ROM desktop, it works fine.
When I am in TWRP, it no longer shows files like it used to.
Back there somewhere I believe I did something and it stopped working.
Now I get Moto G 2015, but no files. Clicking on mount does nothing. 

Can you help me get back connectivity?

lsblk : first one is with phone connected, second one is with phone disconnected.
```
kris@kris-Z97X-UD3H:~$ lsblkNAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0  83.8M  1 loop /snap/core/3748
loop1    7:1    0   130M  1 loop /snap/nutty/10
loop2    7:2    0  83.8M  1 loop /snap/core/3604
loop3    7:3    0  83.7M  1 loop /snap/core/3440
sda      8:0    0 232.9G  0 disk 
&#9500;&#9472;sda1   8:1    0 109.4G  0 part /
&#9492;&#9472;sda2   8:2    0  11.7G  0 part [SWAP]
sdb      8:16   0 596.2G  0 disk 
&#9500;&#9472;sdb3   8:19   0     1K  0 part 
&#9500;&#9472;sdb5   8:21   0  30.3G  0 part /media/E
&#9500;&#9472;sdb6   8:22   0  30.3G  0 part 
&#9500;&#9472;sdb7   8:23   0 271.5G  0 part 
&#9492;&#9472;sdb8   8:24   0 200.5G  0 part /work
sdc      8:32   0 931.5G  0 disk 
&#9492;&#9472;sdc1   8:33   0 931.5G  0 part 
sdd      8:48   0 111.8G  0 disk 
&#9500;&#9472;sdd1   8:49   0   100M  0 part 
&#9500;&#9472;sdd2   8:50   0  63.6G  0 part 
&#9500;&#9472;sdd3   8:51   0     1K  0 part 
&#9492;&#9472;sdd5   8:53   0  35.6G  0 part 
sr0     11:0    1  1024M  0 rom  
kris@kris-Z97X-UD3H:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0  83.8M  1 loop /snap/core/3748
loop1    7:1    0   130M  1 loop /snap/nutty/10
loop2    7:2    0  83.8M  1 loop /snap/core/3604
loop3    7:3    0  83.7M  1 loop /snap/core/3440
sda      8:0    0 232.9G  0 disk 
&#9500;&#9472;sda1   8:1    0 109.4G  0 part /
&#9492;&#9472;sda2   8:2    0  11.7G  0 part [SWAP]
sdb      8:16   0 596.2G  0 disk 
&#9500;&#9472;sdb3   8:19   0     1K  0 part 
&#9500;&#9472;sdb5   8:21   0  30.3G  0 part /media/E
&#9500;&#9472;sdb6   8:22   0  30.3G  0 part 
&#9500;&#9472;sdb7   8:23   0 271.5G  0 part 
&#9492;&#9472;sdb8   8:24   0 200.5G  0 part /work
sdc      8:32   0 931.5G  0 disk 
&#9492;&#9472;sdc1   8:33   0 931.5G  0 part 
sdd      8:48   0 111.8G  0 disk 
&#9500;&#9472;sdd1   8:49   0   100M  0 part 
&#9500;&#9472;sdd2   8:50   0  63.6G  0 part 
&#9500;&#9472;sdd3   8:51   0     1K  0 part 
&#9492;&#9472;sdd5   8:53   0  35.6G  0 part 
sr0     11:0    1  1024M  0 rom  
kris@kris-Z97X-UD3H:~$ 

```

piece of lsblk if I plug in a flash drive:
```
sde      8:64   1   7.2G  0 disk &#9500;&#9472;sde1   8:65   1   194M  0 part /media/kris/2.5.0-25-amd64
&#9492;&#9472;sde2   8:66   1   3.1M  0 part 



```


```
kris@kris-Z97X-UD3H:~$ sudo fdisk -l[sudo] password for kris: 
Disk /dev/loop0: 83.8 MiB, 87863296 bytes, 171608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop1: 130 MiB, 136286208 bytes, 266184 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop2: 83.8 MiB, 87896064 bytes, 171672 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop3: 83.7 MiB, 87793664 bytes, 171472 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0a2c0265


Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *        20480 229396479 229376000 109.4G 83 Linux
/dev/sda2       229396480 253972479  24576000  11.7G 82 Linux swap / Solaris




Disk /dev/sdb: 596.2 GiB, 640135028736 bytes, 1250263728 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x655272b9


Device     Boot     Start        End    Sectors   Size Id Type
/dev/sdb3       133558209 1250256895 1116698687 532.5G  f W95 Ext'd (LBA)
/dev/sdb5       133558272  197046271   63488000  30.3G  7 HPFS/NTFS/exFAT
/dev/sdb6       197048320  260536319   63488000  30.3G  7 HPFS/NTFS/exFAT
/dev/sdb7       260538368  829843455  569305088 271.5G  7 HPFS/NTFS/exFAT
/dev/sdb8       829845504 1250256895  420411392 200.5G 83 Linux








Disk /dev/sdc: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x000bba90


Device     Boot Start        End    Sectors   Size Id Type
/dev/sdc1        2048 1953523711 1953521664 931.5G  7 HPFS/NTFS/exFAT




Disk /dev/sdd: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xcb3adde3


Device     Boot     Start       End   Sectors  Size Id Type
/dev/sdd1  *         2048    206847    204800  100M  7 HPFS/NTFS/exFAT
/dev/sdd2          208845 133558220 133349376 63.6G  7 HPFS/NTFS/exFAT
/dev/sdd3       133564416 208186334  74621919 35.6G  f W95 Ext'd (LBA)
/dev/sdd5       133564480 208186334  74621855 35.6G  7 HPFS/NTFS/exFAT
kris@kris-Z97X-UD3H:~$ 



```

---

### Post by gemmathetechie on 2018-01-05
This might be a little bit outside of your comfort zone (But I'm assuming) have you got adb tools installed on your distro?

If so, have you tried connecting your phone to your PC via adb instead of via your file manager?

---

### Post by Kris_M on 2018-01-05
> **gemmathetechie said:**
> This might be a little bit outside of your comfort zone (But I'm assuming) have you got adb tools installed on your distro?

If so, have you tried connecting your phone to your PC via adb instead of via your file manager?

Thanks! Not at all outside my comfort zone but I only use it to flash recovery, sometimes. However I was very surprised to find it showing a device - last time I checked it didn't - so how to I access files?

EDIT: my goal would be to be able to copy a file from PC onto either internal storage or my 64GB SDcard. )ie I forgot to copy something to my phone and I've already wiped my ROM - yeah, I can restore the ROM and re-boot to it and do  the copy, but I'm lazy! :)  eg the other day I was flashing stuff and I thought I had already copied the zip to the phone so I booted to recovery and wiped and then discovered - DUH!


```
kris@kris-Z97X-UD3H:~$ adb devicesList of devices attached
* daemon not running. starting it now on port 5037 *
* daemon started successfully *
ZY222ZKSLM    recovery


kris@kris-Z97X-UD3H:~$ 



```




EDIT
found adb shell
then ls
then cd sdcard

cool but where is my PC?

in linux of course but need to find it before shell
how end shell
exit
now find item on PC

------------

EDIT2:
Okay, this is easy
On PC copy zip from mounted drive to, say, Downloads.
If I need to find out where stuff is on the phone I can do adb shell and ls , and poke around.
Then just adb push AOSP* /sdcard - - - - - to copy to internal storage, or
adb push AOSP* /external - - - - - to copy to SDcard.

In this case the zip is named AOSP........ .

Easy!!!  Thanks!!!!! Solved!!!

---

