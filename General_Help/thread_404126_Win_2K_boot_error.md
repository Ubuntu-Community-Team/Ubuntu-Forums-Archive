---
title: "Win 2K boot error"
date: 2007-04-08
forum: General Help
---

### Post by linuxfan64 on 2007-04-08
Hi,

I just installed a WD 300 GB HD and tried to install both Win2k and Ubuntu 6.10. Both installs appeared to work and I can boot into 6.10 with no problem.

However, when I tried to boot into Windows, I get the following prompt after I select it at the boot menu:

***STOP: 0x0000007B (0x820B8030, 0xC000014F, 0x00000000, 0x00000000 INACCESSIBLE_BOOT_DEVICE

I have no clue on what to do next.

Thanks much.

---

### Post by krussell on 2007-04-08
Hello :-)
Could you be  more specific about the partitions you used for Ubuntu/Windows?

---

### Post by linuxfan64 on 2007-04-08
I'm really new to this. How do I describe the partitions?

---

### Post by confused57 on 2007-04-08
Boot into Ubuntu, open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

and

```
cat /boot/grub/menu.lst
```
menu.lst is short for menu.list

you just need to post the entries to boot Ubuntu & Windows for the last command

---

### Post by Mr_Mischif on 2007-04-08
> **linuxfan64 said:**
> Hi,

I just installed a WD 300 GB HD and tried to install both Win2k and Ubuntu 6.10. Both installs appeared to work and I can boot into 6.10 with no problem.

However, when I tried to boot into Windows, I get the following prompt after I select it at the boot menu:

***STOP: 0x0000007B (0x820B8030, 0xC000014F, 0x00000000, 0x00000000 INACCESSIBLE_BOOT_DEVICE

I have no clue on what to do next.

Thanks much.

Problem: Dual-booting with Windows.
Solution: Single-boot Ubuntu.


No I kid, but if you just need windows program compatibility, use wine, or if you *really* need it, use [ReactOS](www.reactos.org). It might work well with the GRUB bootmanager. But I'd double-check your bootmanager is loading the right partition/disk.

---

### Post by linuxfan64 on 2007-04-09
OK, here is the output of sudo fdisk -l

Disk /dev/hda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       16709   134215011    7  HPFS/NTFS
/dev/hda2           16710       36293   157308480   83  Linux
/dev/hda3           36294       36481     1510110    5  Extended
/dev/hda5           36294       36481     1510078+  82  Linux swap / Solaris

and the cat /boot/grub/menu.lst output is:

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows 2000 Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


What next, oh wise one?

---

### Post by confused57 on 2007-04-09
I did a Google search and it sounds like a Window's problem:
[http://www.biermann.org/philipp/STOP_0x0000007B/](http://www.biermann.org/philipp/STOP_0x0000007B/)

Hopefully, someone who has experience with this problem will be able to help you find a solution...sorry I can't help you more.

---

