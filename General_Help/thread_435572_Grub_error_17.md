---
title: "Grub error 17"
date: 2007-05-07
forum: General Help
---

### Post by Pink_ on 2007-05-07
Heres the problem as is...
I installed off a usb flash drive because I just don't have a cable for a cd drive.  Install went ok, only minor problems.  When I went to reboot it says something like loading grub, then it says Grub error 17.  I never get to a menu option or anything like that.  BTW I did try swifting through the forum looking for a solution.  Right now I'm booting off the "live cd" thats on the USB drive.

I have three HD's, one is SATA, and the other two are IDE(PATA if you prefer).  

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdb: 3228 MB, 3228696576 bytes
128 heads, 63 sectors/track, 782 cylinders
Units = cylinders of 8064 * 512 = 4128768 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         781     3148960+   b  W95 FAT32

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1305    10482381    c  W95 FAT32 (LBA)
/dev/sda2            1306        9729    67665780    f  W95 Ext'd (LBA)
/dev/sda5            1306        2080     6225156    b  W95 FAT32
/dev/sda6            2081        9729    61440561    7  HPFS/NTFS

Disk /dev/hdc: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        2188    17575078+  83  Linux
/dev/hdc2            2189        2675     3911827+   5  Extended
/dev/hdc5            2189        2675     3911796   82  Linux swap / Solaris

Disk /dev/sdb: 1039 MB, 1039663104 bytes
17 heads, 32 sectors/track, 3732 cylinders
Units = cylinders of 544 * 512 = 278528 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3733     1015280    6  FAT16

sda1 is winXP
sdb is the flash drive
hdc1 is where linux is/should be.
hdb has an old copy of win2k, and its the boot drive
sda refused to be a boot drive when I built this computer(not sure might be something wrong with that section of the drive)
All the rest are junk or swap file drives.

Edit: Its now 3am, I'll be back tomorrow afternoon

---

### Post by Pink_ on 2007-05-07
14 hours, 30 views, and not a single one of you could tell me grub was just looking on the wrong disk?  Just a boot order problem, left grub alone and changed the boot order in the bios, then just edited the windows files to match the new configuration.

---

### Post by rbmorse on 2007-05-07
We knew, we just thought we'd wait for your snotty reply.

---

