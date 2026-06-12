---
title: "Grub help needed after upgrade"
date: 2008-05-07
forum: General Help
---

### Post by drunkrd on 2008-05-07
Hi, I just upgraded one of my 2 Ubuntu partitions from 7.04 to 8.04 and I cant get it running...

Details:

[COLOR="Red"]fdisk -l returns:
[/COLOR]
Disk /dev/hdc: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4661    37439451   83  Linux
/dev/hdc2            4662        4866     1646662+   5  Extended
/dev/hdc5            4662        4866     1646631   82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2632    21141508+   7  HPFS/NTFS
/dev/sda2            2633       14910    98623035    c  W95 FAT32 (LBA)
/dev/sda3           17462       19247    14346045   83  Linux
/dev/sda4           19248       19457     1686825   82  Linux swap / Solaris


When I run the command[COLOR="Red"] "find /boot/grub/stage1"[/COLOR] command in grub, I get this result:
(hd0,0)
(hd1,2)


The boot device in the BIOS is set to the "sda" hard disk...


When I select this Ubuntu installation (this is not the one I upgraded), it runs fine:

(from the menu.lst file)
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=61adf449-3d9b-4a04-b7c6-e8f8df8e1d7d ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault


...and this one is not working:
title 		Linux 8.04 
root		(hd1,0)
kernel  	/boot/vmlinuz-2.6.24-16-generic root=UUID=d666a60b-2edc-4dcc-b28e-6cf1b23adac1 
initrd		/boot/initrd.img-2.6.24-16-generic
quiet


Could you explain me what do I need to change in the menu.lst to get the 8.04 running?

---

### Post by ghost_ryder35 on 2008-05-07
> **drunkrd said:**
> Hi, I just upgraded one of my 2 Ubuntu partitions from 7.04 to 8.04 and I cant get it running...

Details:

[COLOR=Red]fdisk -l returns:
[/COLOR]
Disk /dev/hdc: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
[B]/dev/hdc1   *           1        4661    37439451   83  Linux
/dev/hdc2            4662        4866     1646662+   5  Extended
/dev/hdc5            4662        4866     1646631   82  Linux swap / Solaris[/B]

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2632    21141508+   7  HPFS/NTFS
/dev/sda2            2633       14910    98623035    c  W95 FAT32 (LBA)
[B]/dev/sda3           17462       19247    14346045   83  Linux
/dev/sda4           19248       19457     1686825   82  Linux swap / Solaris[/B]


When I run the command[COLOR=Red] "find /boot/grub/stage1"[/COLOR] command in grub, I get this result:
(hd0,0)
(hd1,2)


The boot device in the BIOS is set to the "sda" hard disk...


When I select this Ubuntu installation (this is not the one I upgraded), it runs fine:

(from the menu.lst file)
title        Ubuntu, kernel 2.6.20-16-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=61adf449-3d9b-4a04-b7c6-e8f8df8e1d7d ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet
savedefault


...and this one is not working:
title         Linux 8.04 
root        (hd1,0)
kernel      /boot/vmlinuz-2.6.24-16-generic root=UUID=d666a60b-2edc-4dcc-b28e-6cf1b23adac1 
initrd        /boot/initrd.img-2.6.24-16-generic
quiet


Could you explain me what do I need to change in the menu.lst to get the 8.04 running?
Which one of the above is your messed up ubuntu install?  Also what does it say when you try to boot into the Linux 8.04 option ?

---

### Post by drunkrd on 2008-05-07
The 8.04 is the messed up install...
/dev/hdc1 * 1 4661 37439451 83 Linux
/dev/hdc2 4662 4866 1646662+ 5 Extended
/dev/hdc5 4662 4866 1646631 82 Linux swap / Solaris



The error message is:
Error 18: Selected cylinder exceeds maximum supported by BIOS.

---

