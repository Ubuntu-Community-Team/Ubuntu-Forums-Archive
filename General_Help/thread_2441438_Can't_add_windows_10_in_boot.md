---
title: "Can't add windows 10 in boot"
date: 2020-04-23
forum: General Help
---

### Post by mauzepaus on 2020-04-23
Hello,

First of all, I have a 2TB SSD, with a 1.5TB Windows 10 partition and a 0.5TB Ubuntu 18.04 partition.
When I start my PC, it shows the boot menu with Ubuntu as the only option.
I have tried os-prober, it didn't work, and boot-repair, with this outcome:[http://paste.ubuntu.com/p/md9TWcgv9h/](http://paste.ubuntu.com/p/md9TWcgv9h/).
I have also tried adding the windows 10 option manually with grub-customizer:
This is my 40_custom document:

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 10 (loader)"{
        insmod part_gpt
        search --no-floppy --set=root --fs-uuid nvme0n1p2
        chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}


And these are my partitions:

```
Disk /dev/loop0: 456.4 MiB, 478527488 bytes, 934624 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 2 MiB, 2076672 bytes, 4056 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 105.2 MiB, 110288896 bytes, 215408 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 140.7 MiB, 147501056 bytes, 288088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 61.5 MiB, 64479232 bytes, 125936 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 2 MiB, 2076672 bytes, 4056 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 456.4 MiB, 478568448 bytes, 934704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 174.8 MiB, 183242752 bytes, 357896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/nvme0n1: 1.9 TiB, 2048408248320 bytes, 4000797360 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 6C2E55E9-3E70-4027-AD5E-B69057040E0A

Device              Start        End    Sectors   Size Type
/dev/nvme0n1p1       2048      34815      32768    16M Microsoft reserved
/dev/nvme0n1p2      34816 2981297511 2981262696   1.4T Microsoft basic data
/dev/nvme0n1p3 2981310576 3924289647  942979072 449.7G Microsoft basic data
/dev/nvme0n1p4 2981298176 2981310463      12288     6M BIOS boot

Partition table entries are not in disk order.


Disk /dev/loop8: 132 KiB, 135168 bytes, 264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 55 MiB, 57614336 bytes, 112528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 141.5 MiB, 148332544 bytes, 289712 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 78 MiB, 81809408 bytes, 159784 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 165.3 MiB, 173293568 bytes, 338464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop13: 62.1 MiB, 65105920 bytes, 127160 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop14: 456.4 MiB, 478564352 bytes, 934696 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop15: 55.4 MiB, 58089472 bytes, 113456 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop16: 74 MiB, 77565952 bytes, 151496 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop17: 57.3 MiB, 60096512 bytes, 117376 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop18: 132 KiB, 135168 bytes, 264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop19: 226.3 MiB, 237326336 bytes, 463528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop20: 172 MiB, 180338688 bytes, 352224 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop21: 93.8 MiB, 98336768 bytes, 192064 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop22: 93.9 MiB, 98484224 bytes, 192352 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop23: 54.8 MiB, 57479168 bytes, 112264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop24: 226.4 MiB, 237375488 bytes, 463624 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop25: 160.2 MiB, 167931904 bytes, 327992 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop26: 58.9 MiB, 61710336 bytes, 120528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop27: 54.7 MiB, 57294848 bytes, 111904 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop28: 140.7 MiB, 147501056 bytes, 288088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


```

 
 Help would be very appreciated!

---

### Post by oldfred on 2020-04-23
You have Windows in UEFI boot mode on gpt partitioned drive.
But now show grub in gpt's protective MBR and a bios_grub partition for Ubuntu to boot in the old BIOS boot mode.
How you boot install media UEFI or BIOS, is then how it installs.
UEFI and BIOS are not compatible. Once you start to boot in one mode or the other, you cannot switch. Or grub can only boot other installs in same boot mode.

Script is not showing an ESP - efi system partition which is FAT32.
And it shows Windows is hibernated/fast start up on.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)


Windows only boots in UEFI mode from gpt, so where is ESP?
Without that neither Windows will never boot.

You can either reinstall or use Boot-Repair when live installer is in UEFI boot mode and totally uninstall grub & reinstall grub.
You can also from inside your BIOS boot, add the UEFI version of grub and install grub again in UEFI boot mode. Bit easier with Boot-Repair.

---

### Post by yancek on 2020-04-23
I doubt that you read the Ubuntu documentation on dual booting UEFI with wndows 10 which is at the link below.  Start there.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> search --no-floppy --set=root --fs-uuid nvme0n1p2 

Not sure where that came from.  "nvme0n1p2" is not a UUID.  The correct UUID for that partition would be the vfat EFI partition which you don't have?? 
That won't help as you installed incorrectly as pointed out above.  The link above explains all this.  If you have deleted your EFI partition you are going to have serious problems 
so it might be easier to do a total re-install of Ubuntu UEFI or at least re-install Grub correctly.

---

