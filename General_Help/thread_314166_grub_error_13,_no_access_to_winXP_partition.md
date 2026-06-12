---
title: "grub error 13, no access to winXP partition"
date: 2006-12-07
forum: General Help
---

### Post by gabams on 2006-12-07
Hi,

I installed ubuntu 6.10 yesterday on a computer that already had Windows XP, and I now have a problem accessing my Windows XP partition. When Grub loads and that I try to boot XP, I get 
[FONT="Courier New"]
Error 13 : Invalid or unsupported executable format[/FONT]

Moreover, when I try to mount manually my XP partition (which is ntfs) in Ubuntu, I get:
[FONT="Courier New"]
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/FONT]

Running fdisk -l gives me:
[FONT="Courier New"]
Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3206    25752163+   7  HPFS/NTFS
/dev/hda2            3207        4792    12739545   83  Linux
/dev/hda3            4793        4864      578340    5  Extended
/dev/hda5            4793        4864      578308+  82  Linux swap / Solaris
[/FONT]

And my /etc/fstab is:
[FONT="Courier New"]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=de562f70-2bce-45cd-8cfc-51aaf4aa1dc0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=C250C51950C514D7 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=8f9b449f-f37f-4dab-8877-b7db8df9ffa6 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
[/FONT]

The Windows part in my /boot/grub/menu.lst is :
[FONT="Courier New"]
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
[/FONT]

Does anybody have an idea of what I should do to be able to access my Windows partition ? 
Thanks a lot for your help !



EDIT : I forgot to tell you that when I do dmesg |tail a I get:

[17181575.980000] NTFS-fs warning (device hda1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17181575.980000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17181575.980000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17181575.980000] NTFS-fs error (device hda1): ntfs_fill_super(): Not an NTFS volume.
[17182153.840000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17182153.844000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17182153.844000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17182153.844000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17182153.848000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17182153.848000] psmouse.c: issuing reconnect request

---

### Post by Sef on 2006-12-07
> 13 : Invalid or unsupported executable format
    This error is returned if the kernel image being loaded is not recognized as Multiboot or one of the supported native formats (Linux zImage or bzImage, FreeBSD, or NetBSD).

I am wondering if you GRUB was not installed correctly.

Try [Restore GRUB]("http://doc.gwos.org/index.php/Restore_Grub") and see if that works.

---

### Post by gabams on 2006-12-07
Thanks for your answer.
I've just tried to follow the steps indicated in your link to restore GRUB, but I realized after that as I was using Ubuntu 6.10, I would have to use Super Grub Disk. However, when I booted with the installation CD of Ubuntu 6.10 and clicked on "install", at the point where I did "manually partition", my windows partition is marked with a "!" in a yellow triangle, and when I double click on it I get :

Unable to detect filesystem. Possible reasons are :
-the filesystem is damaged
-the filesystem is unknown to Gparted
-there is no filesystem available (unformatted)

So I guess that GRUB is correctly installed and that my windows partition is damaged ???? Could I have damaged it by trying to mount it manually at one point ??? And more important, is there a way to repair it ? Or at least to access it at one point, so that I could save 2 or 3 files that I have on it, even if I have to reinstall my windows in the end ?

---

### Post by kainino on 2006-12-13
I have had GRUB error 13 once, and I used a [_Smart Boot Manager Floppy_]("http://slackware.at/data/slackware-current/rootdisks/sbootmgr.dsk") to boot back to Windows (although before I did that I had to delete the Ubuntu partition because Windows wouldn't support multiple partitions, but thats another story), then installed [_OSL2000_]("http://www.osloader.com/") to run instead of GRUB (although I *think* grub may still be installed, just that OSL2000 loads first). I did reinstall GRUB once after that, but it still didn't work.

I have heard that if you have your Windows Recovery CD (which I don't have) that you can type the following commands into the recovery console (select R?) to reinstall the default Windows bootloader:

fdisk /mbr
and/or
fixmbr <device>
and/or
fixboot <drive>

refer to [_gentoo-wiki.com_]("http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why#Boot_sector_.26_MBR_problems") for more help

EDIT: I read [_here_]("http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html") to "Install GRUB on the first sector of the /boot partition. DO NOT INSTALL IT ON THE MBR!." just in case you did.

---

### Post by gabams on 2006-12-14
Thanks. Actually I solved the problem yesterday ! Here is how I did, just in case it can help someone...
I used testdisk ([http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)) to repair my windows boot sector, which was apparently damaged. This did not allow me to boot windows again, but at least I could mount my windows partition again in my Linux. Then I copied everything I had on my windows partition on my Linux partition, and reinstalled windows. Once windows was reinstalled, I used the Super Grub Disk ([http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)) to have GRUB again. 
There might be a more elegant way to do everything I did, but I am completely new to Linux...

---

