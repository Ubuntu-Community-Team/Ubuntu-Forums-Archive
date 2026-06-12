---
title: "Dual Boot Error from Windows after installing GRUB"
date: 2008-06-12
forum: General Help
---

### Post by JibberFisch on 2008-06-12
So I recently tried to install from scratch on a drive (after Windows mysteriously
formatted ALL my partitions) both Windows and Hardy.  Having heard that Windows is
notoriously hard to get on after another OS is present, I installed it first, then booted
the Ubuntu Live CD and installed via gui after partitioning the drive into two equal
halves.  Ubuntu is working fine, but Windows now refuses to boot, saying:

"A problem has been detected and Windows has been shut down to prevent damage to our
computer."

And continues to tell me to run CHKDSK, which I have, getting the following results:

"The volume appears to contain one or more unrecoverable problems."

I'm thinking that maybe Windows is freaking out that GRUB is in its way.  I've looked all
over for feasible answers.  I'd rather not have to reinstall Windows as it has tended in
the past to format more than it should and cause nightmares and sleep loss.  Below are
the results for the menu.lst and fdisk -l:

> title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=c144e237-a5ac-4d5b-a2bb-6b2bddf9d6b3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=c144e237-a5ac-4d5b-a2bb-6b2bddf9d6b3 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c144e237-a5ac-4d5b-a2bb-6b2bddf9d6b3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c144e237-a5ac-4d5b-a2bb-6b2bddf9d6b3 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
 

> Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/sda2           16709       16928     1767150   83  Linux
/dev/sda3           16929       38913   176594512+   5  Extended
/dev/sda5           16929       38163   170570106   83  Linux
/dev/sda6           38164       38913     6024343+  82  Linux swap / Solaris


Thank you so much, I've been beating my head against the wall trying to solve this one. :confused:

---

