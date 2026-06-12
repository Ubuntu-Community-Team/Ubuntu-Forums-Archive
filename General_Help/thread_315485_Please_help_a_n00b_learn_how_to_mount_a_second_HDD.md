---
title: "Please help a n00b learn how to mount a second HDD"
date: 2006-12-09
forum: General Help
---

### Post by Cerberus 81 on 2006-12-09
I'm running Ubuntu Dapper on a self-built budget PC; primary hard drive is on the primary IDE channel, while the second HDD (for media/music files) is on a SATA connection.  The mainboard uses a VIA K8M800 chipset with VIA's VT8237R southbridge.  The second HDD ( /dev/sda1 )shows up with the other volumes (main HDD, DVD, floppy) in File Browser's "Computer" window, but attempts to access files on the drive end with the error message "Unable to mount the selected volume". Running the "fdisk -l" command in Terminal yields the following:
> root@****-desktop:~# sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14593   117218241    c  W95 FAT32 (LBA)

Disk /dev/hda: 20.0 GB, 20060135424 bytes
255 heads, 63 sectors/track, 2438 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2335    18755856   83  Linux
/dev/hda2            2336        2438      827347+   5  Extended
/dev/hda5            2336        2438      827316   82  Linux swap / Solaris

Disk /dev/sdb: 1031 MB, 1031798784 bytes
16 heads, 32 sectors/track, 3936 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3936     1007600    6  FAT16
root@****-desktop:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

The inability to mount occurs whether the mainboard's SATA mode is set to IDE or RAID in BIOS.  Does anyone have input on this problem?

---

### Post by bscbrit on 2006-12-09
Create a mount point:

sudo mkdir /media/sata_disk

mount it:

sudo mount -t VFAT /dev/sda1 /media/sata_disk


When you have got it to successfully mount, proving that there is no hardware fault, then modify your fstab to mount it at boot time.

Or have I misunderstood....?

---

### Post by bernied on 2006-12-09
Have a look at dmesg just after you try to mount the drive:
```
dmesg | tail
```
Post the output here
Perhaps you need to install smbfs

---

### Post by Cerberus 81 on 2006-12-09
> **bernied said:**
> Have a look at dmesg just after you try to mount the drive:
```
dmesg | tail
```
Post the output here
Perhaps you need to install smbfs

Okay, just looked at the output from the dmesg command:
> [17179634.044000] /dev/vmnet: port on hub 1 successfully opened
[17179634.048000] /dev/vmnet: open called by PID 5340 (vmnet-netifup)
[17179634.048000] /dev/vmnet: port on hub 8 successfully opened
[17179634.400000] /dev/vmnet: open called by PID 5364 (vmnet-dhcpd)
[17179634.400000] /dev/vmnet: port on hub 1 successfully opened
[17179634.420000] /dev/vmnet: open called by PID 5366 (vmnet-dhcpd)
[17179634.420000] /dev/vmnet: port on hub 8 successfully opened
[17179640.520000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17179644.444000] vmnet1: no IPv6 routers present
[17179644.508000] vmnet8: no IPv6 routers present


Apologies for forgetting to mention that the media HDD is formatted as FAT32 in my initial post.  About to try the steps that bscbrit suggested...

---

### Post by Cerberus 81 on 2006-12-09
> **bscbrit said:**
> Create a mount point:

sudo mkdir /media/sata_disk

mount it:

sudo mount -t VFAT /dev/sda1 /media/sata_disk


When you have got it to successfully mount, proving that there is no hardware fault, then modify your fstab to mount it at boot time.

Or have I misunderstood....?

Worked like a charm -- thanks :)   As for modifying fstab, I'm a bit beyond my level of competence; file system would obviously be /dev/sda1 and mount point would obviously be /media/sata_disk as you stated, but I'm unsure what criteria should be entered for the type, options, dump, & pass categories... "type" appears to be synonymous with file-system so perhaps I would enter fat32, but I've no clue for the final three categories.

---

### Post by bscbrit on 2006-12-09
These links should answer all your questions:

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

Good Luck.

---

### Post by bscbrit on 2006-12-09
At the command line, type 

man mount

It will answer a lot more questions, but it takes reading a few times.  A great deal of linux information is already on your computer.  Type 'man ....' and the command you would like to learn about - its probably already there. ;)

---

