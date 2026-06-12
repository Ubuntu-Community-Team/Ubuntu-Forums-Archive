---
title: "GRUB Hard Disk Error !!"
date: 2008-05-10
forum: General Help
---

### Post by zipped on 2008-05-10
Hello !!

Sorry to interrupt for those who doesn't like to be intterupted..

I have some problems regardings GRUB. In these few days i have been trying to figure out the problem, but i don't know how :).

The problem started a few days ago when i delete some partition. I have to IDE hard drives, the first hard drive is used for Windows XP and its second partition C: and D:. The second hard drives is used for Linux distro. Currently i have two distro available first is Mandriva 2008.1 and Ubuntu 8.04 Hardy. 

But here come the main problem when i started to have a GRUB Hard Disk Error when try to boot to XP. I believe its a hd0,0 in GRUB. I try again to use test disk from CGSecurity to repair the boot sector and so on, but the problem still persist as i am unable to boot again for XP. I also tried to use super GRUB, LILO, but as i try to boot to Windows XP, the message always appear as GRUB Hard Disk Error and freeze. I already tried **fdisk /mbr** and the result is just black screen with GRUB Hard Disk Error messages.

Is there anyone that can gives me a solution for this problem and how to fix this annoying GRUB Hadr Disk Error ?? 

For information I'm currently using two ide hard drives. 

1.HD1 Windows XP and its second partition. SIZE 120GB  (MASTER)
2.HD2 Linux Mandriva 2008.1 with Ubuntu 8.04 + Swap file and additional free space. SIZE 160GB (SLAVE).

If someone needs additional info for solving this problem i can try to fulfill it with my best. :)

---

### Post by zipped on 2008-05-10
Uhhuu...FDISK -l report 

```

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7443    59785866    7  HPFS/NTFS
/dev/hda2            7444       14593    57432375    f  W95 Ext'd (LBA)
/dev/hda5            7444       14593    57432343+   b  W95 FAT32

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa1efe6fc

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4823    38740716   83  Linux
/dev/hdb2            4824        9825    40178565    5  Extended
/dev/hdb5            4824        5648     6626781   82  Linux swap / Solaris
/dev/hdb6            5649        9825    33551721   83  Linux

Disk /dev/sda: 1031 MB, 1031798272 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         126     1007584    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(124, 254, 63) logical=(125, 112, 50)

```

---

