---
title: "Drive unmountable, but partition visible in XP"
date: 2007-12-08
forum: General Help
---

### Post by broozm on 2007-12-08
OK, notso-newbie (I have some exposure to Unix in the old days  -- if writing my first webpage in vi counts!??!:)

Problem: 200GB PATA drive will not mount. It has Windows2000 NTFS data on it that I would like, nay neeed.

I have attached it on the secondary IDE as slave (I think)

sudo fdisk -l
gives

Disk /dev/hda: 4327 MB, 4327464960 bytes
255 heads, 63 sectors/track, 526 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         496     3984088+  83  Linux
/dev/hda2             497         526      240975    5  Extended
/dev/hda5             497         526      240943+  82  Linux swap / Solaris

Disk /dev/hdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       24321   195358401    7  HPFS/NTFS


Running "sudo gparted" shows me

Model: ST3200822A
Size: 186.31 GiB
Path: /dev/hdd

DisklabelType: msdos
Heads: 255
Sectors/Track: 63
Cylinders: 24321
Total Sectors: 390716865


Filesystem: unknown
Size: 186.31.GiB
Flags: boot
Path: /dev/hdd1
Status: not mounted

First Sector: 63
Last sector: 390716864
Total Sectors: 390716802
 Warning: Unable to detect filesystem! Possible reasons are:
the filesystem is damaged
the filesystem is unknown to GParted
There is no filesystem available (unformatted)


1
If I boot to Windows (XP), I can see a SECOND (smaller) partition - and I think the first large partition is the "missing" one

2
Am I correct in thinking I cannot runn dd (ar anything else to get data off until it is mounted?)

3
I have run BootITNG and tried to recreate the standard MBR

4
Have not tried XP or W2k fixmbr etc (as there was no bootable OS on the disk (it was just data)

5
I have installed testdisk, but it requires a reboot - not yet done (Does this sound correct by the way that it needs a reboot to work?)

6
All of these commands give me "permission denied"
fixntfs hdd
fixntfs hdd1
fixntfs hdd2
sudo fixntfs hdd

:(

HELP

Bruce

---

### Post by bingoUV on 2007-12-08
Filesystem seems to be corrupt. As it is NTFS,  windows should help you fix it.

2. You can run dd on /dev/hdd1 without mounting it. But it would not give you the files, just the raw bytes from the device. By this, you could backup your whole partition. This will be needed to restore in case you are trying risky ways to fix your NTFS partition and it gets corrupted further. 

3,4. MBR is only used for booting. Even if you fix MBR for this drive, it will not help you recover the data. So drop this idea.

6. Actually you need to fix the filesystem on the device /dev/hdd1. I don't know about fixntfs. Is it the same as ntfsfix from ntfs-progs package? If yes, you need 
```

sudo fixntfs /dev/hdd1

```

---

### Post by broozm on 2007-12-09
2
Can't seem to get anything out of dd - does the result below mean that no matches to the text were found ?

```
badmin@badmin-desktop:~$ sudo dd if=/dev/hdd count=100 bs=512 | grep -i "Accounts"
Password:
100+0 records in
100+0 records out
51200 bytes (51 kB) copied, 0.0346511 seconds, 1.5 MB/s
badmin@badmin-desktop:~$ sudo dd if=/dev/hdd bs=512 | grep -i "Accounts"
Binary file (standard input) matches
badmin@badmin-desktop:~$ sudo dd if=/dev/hdd bs=512 | grep -i "a"
Password:
Binary file (standard input) matches
badmin@badmin-desktop:~$ sudo dd if=/dev/hdd count=100000000 bs=512 | grep -i "Accounts"
Binary file (standard input) matches
badmin@badmin-desktop:~$ 
```

(Rather than copy the entire disk, I was looking for a few folders.. or even files. but will copy the whole thing prior to letting Windows loose:)


6
fixntfs ran yesterday (now that I have run 169 Ubuntu updates - it no longer does!?)
I found this command described on this forum: [http://ubuntuforums.org/showthread.php?t=490833](http://ubuntuforums.org/showthread.php?t=490833)


7
The syslog [below] shows that hdd has differing current and native capacities - if that means anything?
The CDROM is the slave on IDE1, and the bad disk is on ide2 on its own to simplify. It appears to be slave on 2 - but as I have no master - could this be an issue. It is using an old 40 ribbon cable. Note that my mobo has 4 ides.

What worries me is that I can see second (small) partition from Windows, but the first is "unformatteed, yet in Ubuntu, I only get hdd (not hdd1 or hdd2).
In File navigator, I do not see the hdd at all, but in device manager it shows as a single "volume, block"

[   43.023145] Probing IDE interface ide3...
[   43.612023] hda: max request size: 128KiB
[   43.651221] hda: 8452080 sectors (4327 MB) w/256KiB Cache, CHS=8944/15/63, UDMA(33)
[   43.651246] hda: cache flushes not supported 
[   43.651365]  hda: hda1 hda2 <<6>usb 1-1: configuration #1 chosen from 1 choice
[   43.690112]  hda5 >
[   43.690540] hdd: max request size: 512KiB
[   43.696603] hdd: Host Protected Area detected. 
[   43.696611]  current capacity is 390719855 sectors (200048 MB)
[   43.696616]  native  capacity is 390721968 sectors (200049 MB)
[   43.697003] hdd: Host Protected Area disabled.
[   43.697017] hdd: 390721968 sectors (200049 MB) w/8192KiB Cache, CHS=24321/255/63, UDMA(33) 
[   43.697183] hdd: cache flushes supported
[   43.697312]  hdd:<6>hdb: ATAPI 32X CD-ROM drive, 128kB Cache, UDMA(33)
[   43.697480] Uniform CD-ROM driver Revision: 3.20
[   43.700630]  hdd1
[   43.957947 ] usbcore: registered new interface driver hiddev
[   44.006371] input: HID 04b4:0407 as /class/input/input2

> **bingoUV said:**
> Filesystem seems to be corrupt. As it is NTFS,  windows should help you fix it.

2. You can run dd on /dev/hdd1 without mounting it. But it would not give you the files, just the raw bytes from the device. By this, you could backup your whole partition. This will be needed to restore in case you are trying risky ways to fix your NTFS partition and it gets corrupted further. 

3,4. MBR is only used for booting. Even if you fix MBR for this drive, it will not help you recover the data. So drop this idea.

6. Actually you need to fix the filesystem on the device /dev/hdd1. I don't know about fixntfs. Is it the same as ntfsfix from ntfs-progs package? If yes, you need 
```

sudo fixntfs /dev/hdd1

```

---

