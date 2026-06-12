---
title: "please help me edit grub"
date: 2008-01-02
forum: General Help
---

### Post by benner on 2008-01-02
i have 3 hard disks; in boot order in the BIOS they are:
sda1
hda1
sdb1

sda1 has ubuntu and grub.  hda1 has xp64 and sdb1 has xp32.

i get grub options at boot, select ubuntu and it boots fine.  if i select xp64, i (currently) get "starting up...) and then nothing.  i have rebooted into ubuntu and changed the numbers in grub a bunch of times (hd1,0...hd1,1...hd2,0...hd2,1 and so on) and i either get the expected errors (no such partition) or i get the 'starting up...) and then nothing.  i have edited it the same way in the past and it worked so i must have missed something silly.  please help if you can.

the current state of things...

here's fdisk:


ben@RAMEN-UBUNTU:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3315    26627706   83  Linux
/dev/sda2   *        3316        6630    26627737+  83  Linux
/dev/sda3            6631        6910     2249100   82  Linux swap / Solaris
/dev/sda4            6911       30401   188691457+  83  Linux

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 20.4 GB, 20404101120 bytes
255 heads, 63 sectors/track, 2480 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x63ca63ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2479    19912536    7  HPFS/NTFS

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2580c91d

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       10010    80405293+   7  HPFS/NTFS



here's grub:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=908a2896-3e64-452c-a32b-9721eb40cd28 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=908a2896-3e64-452c-a32b-9721eb40cd28 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows XP 64
root		(hd2,0)
savedefault
makeactive
chainloader	+1

---

### Post by tgilber1 on 2008-01-03
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Windows XP 64
root (hd2,0)
savedefault
makeactive
chainloader +1

below is an example.  Please read the grub manual to verify - you can test these lines by typing directly into grub command line during bootup #ESC#c to get direct grub command.  Assumes that (hd0)=Linux, (hd1)=XP 64, (hd2)=XP 32
----------------------------------------------------------------------------------------------------------------------------

title Windows XP 64
map (hd0) (hd1)
map (hd1) (hd0)
chainloader (hd1,0)+1


title Windows XP 32
hide (hd1,0) #hide windows partition
rootnoverify (hd1,0) #do not mount or verify first windows partition
map (hd0) (hd2)
map (hd2) (hd0)
chainloader (hd2,0)+1


Here's an excerpt from the grub manual that may help

[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)

GRUB cannot boot DOS or Windows directly, so you must chain-load them (see Section
4.1.2 [Chain-loading], page 11). However, their boot loaders have some critical deficiencies,
so it may not work to just chain-load them. To overcome the problems, GRUB
provides you with two helper functions.
If you have installed DOS (or Windows) on a non-first hard disk, you have to use
the disk swapping technique, because that OS cannot boot from any disks but the first one.
The workaround used in GRUB is the command map (see Section 13.3.23 [map], page 46),
like this:
grub> map (hd0) (hd1)
grub> map (hd1) (hd0)
This performs a virtual swap between your first and second hard drive.

---

### Post by benner on 2008-01-03
that worked like a charm.  thank you for taking the time to help me understand why as well.  cheers.

---

