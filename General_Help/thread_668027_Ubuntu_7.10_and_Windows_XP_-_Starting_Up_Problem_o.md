---
title: "Ubuntu 7.10 and Windows XP - Starting Up Problem of XP (Solution)"
date: 2008-01-15
forum: General Help
---

### Post by ilyasyildirim on 2008-01-15
Dear All,

I had this problem and could not find any online solution for it. I solved the problem and therefore want to share it with you guys, in case it can help you, too.

I had a dual boot system; Windows XP and Suse 10.1. I wanted to change the linux operating system to Ubuntu 7.10 and installed Ubuntu over SUSE. When GRUB started, I could not start neither Ubuntu nor Windows XP. This is due to the way grub sees the hard drives I have in my machine.

My system has 3 hard drives; 2 SATA and 1 normal hard disk. Here is the fdisk output:
-------------------------------------------------------------------
anatolia:/boot/grub>sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000081

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9726    78124063+  83  Linux

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf267f267

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3465    27832581    7  HPFS/NTFS
/dev/sdb2            3466        3595     1044225   82  Linux swap / Solaris
/dev/sdb3            3596        9724    49231192+  83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa5850943

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641   83  Linux
anatolia:/boot/grub>
---------------------------------------------------
When I check out the device.map, I see 3 hard drives:

anatolia:/boot/grub>more /boot/grub/device.map 
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc
anatolia:/boot/grub>

This device.map is different than the SUSE output. As far as I remember, I had hdb,sda,sdb in the SUSE device.map. For a system with 2 SATA and 1 normal hard drive, SUSE's device.map is the right one. I am not sure why UBUNTU detected it this way. 

Ubuntu and XP are installed on the same disk, which is /dev/sdb. The /boot/grub/menu.lst had the following sections for UBUNTU and XP:

-----------------------------------------
## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3ed92731-1bcc-442b-a3b0-8031ead35d8a ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3ed92731-1bcc-442b-a3b0-8031ead35d8a ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,2)  
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Home Edition
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
-----------------------------------------

For the above device.map, this grub looks right, but it is not. What I had to do was to change the above menu.lst to following:

-----------------------------------------
## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
**root            (hd0,2)**
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3ed92731-1bcc-442b-a3b0-8031ead35d8a ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
**root            (hd0,2)**
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3ed92731-1bcc-442b-a3b0-8031ead35d8a ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
**root            (hd0,2)**
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Home Edition
**root            (hd0,0)**
savedefault
makeactive 
[B]map             (hd0) (hd0)
map             (hd0) (hd0)[/B]
chainloader     +1
-----------------------------------------

After making these changes, both UBUNTU and Windows XP started without a problem. In some of the forum discussions, they were blaming XP for this problem, but I think it is UBUNTU's problem. There must be a bug, I would say. When I installed the system, UBUNTU did not recognize the hard drives correct; even though I had 2 SATA and 1 normal HD, it saw 3 SATA drives. I think this is what caused this whole problem with the "Starting Up". Hope this thread can help anyone having the some issues.

Ciao,

---

