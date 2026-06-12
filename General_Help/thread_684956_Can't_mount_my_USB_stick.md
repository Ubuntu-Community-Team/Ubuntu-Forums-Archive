---
title: "Can't mount my USB stick"
date: 2008-02-01
forum: General Help
---

### Post by realmcoy on 2008-02-01
So I've just updated to ubuntu 7.10 and inserted my USB stick and it came up with an error message "unable to mount volume... it knows it's there but wont mount it.

I've had no problems mounting in previous version of ubuntu...

any ideas?

---

### Post by taurus on 2008-02-01
Can you post the outputs of these two commands from a terminal?

```
sudo fdisk -l
dmesg | tail
```

---

### Post by realmcoy on 2008-02-01
Thats where things get interesting... I have a speed touch USB adsl broadband modem that no matter how much I try I cant get it to work (i've followed the instructions on [https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch)) so i'll have to go into uni tomorrow and use their wireless internet to post you the script.

Thanks in advance

until tomorrow

realmcoy

---

### Post by realmcoy on 2008-02-02
Hi again,
This is what it says when I click "details" on the unable to mount message

mount: wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program or other error

these are the psudo fdisc -1 and dmesg | tail you asked for:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1e47d573

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1306    10485760   27  Unknown
/dev/sda2   *        1306        7936    53256192    7  HPFS/NTFS
/dev/sda3            7937        8179     1951897+  82  Linux swap / Solaris
/dev/sda4            8180       14593    51520455   83  Linux

Disk /dev/sdb: 4102 MB, 4102889984 bytes
255 heads, 63 sectors/track, 498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         497     3992135+   b  W95 FAT32






[  269.232000] sdb: Mode Sense: 03 00 00 00
[  269.232000] sdb: assuming drive cache: write through
[  269.236000] SCSI device sdb: 8013457 512-byte hdwr sectors (4103 MB)
[  269.236000] sdb: Write Protect is off
[  269.236000] sdb: Mode Sense: 03 00 00 00
[  269.236000] sdb: assuming drive cache: write through
[  269.236000]  sdb: sdb1
[  269.236000] sd 4:0:0:0: Attached scsi removable disk sdb
[  269.236000] sd 4:0:0:0: Attached scsi generic sg1 type 0
[  269.620000] FAT: Unrecognized mount option "usefree" or missing value





hope this helps

realmcoy

---

### Post by taurus on 2008-02-02
Try

```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1
df -h
```

---

### Post by vanadium on 2008-02-02
You might want to check the filesystem

dosfsck /dev/sdb1

(the equivalent of "chkdsk" under Windows). If you see errors, then you probably do not need to look further. Consult "man dosfsck" to see how to repair the disk, or run chkdsk /f on a Windows system.

---

