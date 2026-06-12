---
title: "Vista wants doctor."
date: 2008-05-02
forum: General Help
---

### Post by Meelis on 2008-05-02
Hi

How to fix dual boot? :(
I installed Ubuntu 8.04 64bit, it's fast & nice, but cant boot Vista 64bit now.
My PC specs; Gigabyte P35C-DS3R, C2D e4500, 4gb mem, HD-3870
C: IDE 80gb - Vista Installed on it ntfs
D: SATA 320gb - Ubuntu on it
E: DVD-RW
F: USB2 320gb HDD fat32

When I installed Vista, Vista didn't see SATA drive.
Installed Ubuntu on SATA  (didn't format IDE 80gb).
Now ther isn't boot options, Ubuntu just boots.
In Ubuntu I have total acsess to all drives & files but Vista can't boot, can't bootrec.exe /fixmbr because Vista doesn't show any hdd but can brause drivers from all folders in Vista installed HDD.
When i unplug USB HDD Vista on DVD drive wont boot & ubunto boots (1 boot device is DVD rom 2th too, 3th is HDD).

[INDENT]My sudo gedit /boot/grub/menu.lst[/INDENT]
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3722e57c-e1a3-491f-a3f3-7a4cdeff3d2a ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3722e57c-e1a3-491f-a3f3-7a4cdeff3d2a ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title		Windows Vista 64bit
root		(hd0,1)
savedefault
makeactive
chainloader	+1

**sudo fdisk -l**
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2432    19535008+  83  Linux
/dev/sda2   *       36482       38913    19535040   82  Linux swap / Solaris
/dev/sda3            2433       36481   273498592+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x21d621d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    c  W95 FAT32 (LBA)
:guitar:

---

### Post by warp99 on 2008-05-02
Here is your problem:

```
When i unplug USB HDD Vista on DVD drive wont boot & ubunto boots (1 boot device is DVD rom 2th too, 3th is HDD).
```

When you boot your computer if the BIOS accesses the first hard drive, (root (hd0,0) as boot it can't access the USB drive because the USB drivers have not been loaded by the Ubuntu kernel. You can't chainload boot in that fashion. You need to do one of the following:

a) In your BIOS make the Vista USB drive the primary boot device, then DVD, and then sata drive. So you would plug in the USB drive to boot Vista or un-plug the drive to boot to Ubuntu. This may be a hassle if you have to reset the BIOS all of the time to make the Vista USB drive the first boot device.

b) copy the Vista partition to a new partition on your sata drive, then you can chainload the Vista install as listed in your menu.lst.

c) copy the Vista partition as the primary partition on your sata drive, then restore your Vista MBR and use the Windows bootloader to chainload Ubuntu. 

In order to make the partitions you need to boot to the Ubuntu install disc and use gparted to make and copy the partitions or you can use the gparted LiveCD or LiveUSB to accomplish the same thing. These tools are available here:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by Meelis on 2008-05-03
Thank you for quick replay.

Vista is on the 80gb internal HDD, USB2 HDD fat32 for documents.
Now when i unplug USB HDD, my 1st boot device (dvdrom) wont boot anithing (linux, windows, supergrub).
I can boot frob dvd, then remove usb hdd.

When i start Vista install i can see Vista partitions as primary & Ubuntu partitions also primary.:)

Vista fixmbr didn't work.
I install Vista now.

I'm not :lolflag:

---

