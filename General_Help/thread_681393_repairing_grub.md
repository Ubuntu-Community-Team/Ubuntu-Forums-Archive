---
title: "repairing grub"
date: 2008-01-28
forum: General Help
---

### Post by PatrickRay007 on 2008-01-28
Here's my fdisk -lu output:

pray@pray-laptop:~$ sudo fdisk -lu
[sudo] password for pray:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xedaaedaa

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *   203961240   233054954    14546857+  83  Linux
/dev/hda2       233054955   234436544      690795    5  Extended
/dev/hda4        14346045   203961239    94807597+   7  HPFS/NTFS
/dev/hda5       233055018   234436544      690763+  82  Linux swap / Solaris

Partition table entries are not in disk order


And Here's my menu.lst


kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5ac72566-a113-4305-8ac9-44413a9edfdb ro single
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
# on /dev/hda4
title		Windows NT/2000/XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


I can't get into Windows after I messed around with this, and I'm attempting to reconfigure my menu.lst.  What should i put in the Windows entry to make it so that I'm able to boot into it?  I've googled, and am not sure I understand how this menu.lst file works.  Also, I've got a hidden recovery partition that I cannot access anymore through the Gateway menu (the laptop is a Gateway MX6447), is there a way to access the recovery partition through grub? (just in case...)

---

### Post by PatrickRay007 on 2008-01-29
k, so just an update, in menu.lst under the windows entry I used hd (0,3) because Windows is hda4 and was able to boot into the windows loader, but am still having hal.dll issues.  Anybody got any idea on how to repair that file without wiping grub?  I know I can fdisk mbr, but I'm not too keen on reinstalling grub.  I'd rather not be able to boot into windows than not be able to boot into Ubuntu.  It's just so preeeetttyyy.

---

