---
title: "Lost grub by hitting F8"
date: 2013-05-03
forum: General Help
---

### Post by maglinu on 2013-05-03
Hello,
I have (or had) a dual boot setup - Ubntu 12.04.2 and W7.

I wanted to boot W7 into safe mode - so I hit F8 during start-up, as you do.

Unfortunatley, since I stupidly forgot this is now a dual boot machine it wasn't windows loader that was loading at the time but grub (ie before the grub screen appeared). Grub didn't seem to take kindly to this treatment

Now all I get is:

error:no such partition.
grub rescue>

Perhaps more worryingly, I am now looking at my HDD fromn a live cd, and this what I see in Gparted for the partition where ubuntu should be:
[ATTACH=CONFIG]242133[/ATTACH]
Any help very much appreciated.

---

### Post by maglinu on 2013-05-03
Bit more info in case it is any help:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa189a189

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    24578047    12288000   27  Hidden NTFS WinRE
/dev/sda2   *    24578048    24782847      102400    7  HPFS/NTFS/exFAT
/dev/sda3        24782848   231542783   103379968    7  HPFS/NTFS/exFAT
/dev/sda4       231544830   625141759   196798465    5  Extended
/dev/sda5       616902656   625141759     4119552   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

I still don't see my ubuntu partition at all

---

### Post by maglinu on 2013-05-03
Here is the bootinfoscript output.
```
   Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    24,578,047    24,576,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     24,578,048    24,782,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          24,782,848   231,542,783   206,759,936   7 NTFS / exFAT / HPFS
/dev/sda4         231,544,830   625,141,759   393,596,930   5 Extended
/dev/sda5         616,902,656   625,141,759     8,239,104  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        DAA41C49A41C2B11                       ntfs       PQSERVICE
/dev/sda2        E868D0DA68D0A898                       ntfs       SYSTEM RESERVED
/dev/sda3        7C9AD7DA9AD78ED0                       ntfs       ACER
/dev/sr0                                                iso9660    Ubuntu 12.04.2 LTS i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt

```
I still can't see anything that looks like ubuntu:(

---

### Post by maglinu on 2013-05-03
I have now tried 'ls' at the grub rescue prompt, and gone through all of the 'ls (hd0.msdosx)' combinations offered. None of them produces anything other than 'unknown filesystem'.

Other ideas gratefully recieved.

---

### Post by oldfred on 2013-05-03
f8 on its own should not have removed a partition from partition table.

It looks like you just lost your partition and it now is shown as unallocated.
Testdisk may just recover it.

       [URL="https://help.ubuntu.com/community/DataRecovery"]https://help.ubuntu.com/community/DataRecovery
[/URL][URL="https://help.ubuntu.com/community/DataRecovery#Lost%20Partition"]https://help.ubuntu.com/community/DataRecovery#Lost%20Partition
[/URL]
 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Gparted and parted also has some tools for finding lost partitions, I have not tried those.
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
    [URL="https://help.ubuntu.com/community/DataRecovery#Lost%20Partition"]
[/URL]

[URL="https://help.ubuntu.com/community/DataRecovery"]
[/URL]

---

### Post by maglinu on 2013-05-03
oldfred you are a star!:KS

parted found and restored my partition :)

many thanks
Dave

---

### Post by oldfred on 2013-05-03
Glad you got it back. :)

---

