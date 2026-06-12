---
title: "My flash drive stopped working"
date: 2008-01-17
forum: General Help
---

### Post by GamesForLinux on 2008-01-17
I was playing with QTparted, trying to partition my 500mb flash drive. I couldn't get it to do what I wanted, and then I couldn't access the flash drive at all. The external usb hard drive that was attached also stopped working. Also, another flash drive that hadn't been attached wouldn't work. They still showed up in QTparted, though. They all work fine under windowsXP and another hard drive with Ubuntu 7.04 on it.
I searched the forums and came up with someone with a similar problem: [http://ubuntuforums.org/showthread.php?t=454833& ](http://ubuntuforums.org/showthread.php?t=454833& )
I tried ```
cat /etc/fstab
and
sudo fdisk -l
``` but neither one fixed it. I found a sda and sdb (which corresponded to the labels QTparted gave them) in /dev and tried modifying the code to ```
cat /dev/sda
``` That caused the terminal to beep wildly and flash screens apon screens of unintelligible text until I pulled the flash drive out.
Any help would be apprciated. Thanks!

---

### Post by mathisdermaler on 2008-01-17
The command "cat" means "write this file to the terminal" so it's not surprising that cat /dev/sdb would show you screens of binary data.

Run "sudo fdisk -l" again.  It won't fix anything but it will print some diagnostic messages to your terminal.  Copy that and paste it in this thread, and then we'll have some more info.

---

### Post by GamesForLinux on 2008-01-23
Sorry about the delay.
Here are the results:
(WindowsXP is installed on the 80gb, Ubuntu on the 7.5gb, and the .5gb is the flash drive)

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9732    78172258+   7  HPFS/NTFS

Disk /dev/hdb: 7510 MB, 7510164480 bytes
255 heads, 63 sectors/track, 913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         867     6964146   83  Linux
/dev/hdb2             868         913      369495    5  Extended
/dev/hdb5             868         913      369463+  82  Linux swap / Solaris

Disk /dev/sda: 524 MB, 524288000 bytes
17 heads, 59 sectors/track, 1020 cylinders
Units = cylinders of 1003 * 512 = 513536 bytes

   Device Boot      Start         End      Blocks   Id  System

---

### Post by GamesForLinux on 2008-01-30
You can ignore this post now, I've reinstalled linux.

---

