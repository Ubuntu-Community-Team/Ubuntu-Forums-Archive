---
title: "Grub Error 17"
date: 2005-10-21
forum: General Help
---

### Post by xnotte on 2005-10-21
Hello. I have a disk with 3 partitions. 1: windows ntfs, 2: swap, 3: ext3. When installing ubuntu, after the base installation, when rebooting, i can't boot in any  OS because it gives me a error 17 in GRUB!

I've loaded rescue with ubuntu cd, and re-installed grub, "grub install /dev/hda"  and then "update-grub" and didn't worked. Anyone has any idea ?

---

### Post by aysiu on 2005-10-21
These might help:

[http://www.ubuntuforums.org/showthread.php?t=75417&highlight=error+17+grub](http://www.ubuntuforums.org/showthread.php?t=75417&highlight=error+17+grub)
[http://www.ubuntuforums.org/showthread.php?t=74466&highlight=error+17+grub](http://www.ubuntuforums.org/showthread.php?t=74466&highlight=error+17+grub)
[http://www.ubuntuforums.org/showthread.php?t=72093&highlight=error+17+grub](http://www.ubuntuforums.org/showthread.php?t=72093&highlight=error+17+grub)

---

### Post by xnotte on 2005-10-22
thank you. but none of that helped me.

my partitions are like this:

  Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 -----------------------------------------------------------------------------
   hda1                    Primary   NTFS             []              62914.69*
                           Pri/Log   Free Space                           0.49*
   hda5                    Logical   Linux swap                         509.97
   hda3        Boot        Primary   Linux ext3       [/]             16598.62

and i have this in /boot/grub/menu.lst:

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
boot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


when doing 'grub-install /dev/hda' it says something like this:

root@ttyp1[knoppix]# grub-install --root-directory=/mnt/disco/ /dev/hda
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /mnt/disco//boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/mnt/disco//boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /mnt/disco//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/hda

THANK YOU IN ADVANCE!

---

### Post by xnotte on 2005-10-23
anyone can help me ?! I have a serious problem here :(

---

### Post by xnotte on 2005-10-25
:confused:

---

### Post by indusnecro on 2005-10-25
Try this instead of grub-install /dev/hda
You will get detailed information.

#**grub**

grub> **root (hd0,2)** 
grub> **setup (hd0)**

If the problem is not solved, post the messages you get.

---

