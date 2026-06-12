---
title: "[SOLVED] Using syslinux to boot from 2nd partition...or do I need GRUB?"
date: 2008-05-28
forum: General Help
---

### Post by drewster1829 on 2008-05-28
I'm trying to make a persistent Ubuntu 8.04 LiveUSB setup, but with the ubuntu8 750 MB LiveCD partition as the 2nd, with the first partition as an empty FAT32 (so I can use it as a normal USB stick in an MS Windows machine).

How do I get syslinux to boot /dev/sda2(the 2nd USB drive partition), or can I?  By using "syslinux -sf /dev/sdb2", and then attempting to boot the drive, I get "Missing operating system".  Somehow I need to write to the MBR of the USB stick (4GB micro Cruzer) so that it transfers boot control to /dev/sda2 (or hd(0,1)), but I don't know how with syslinux.

If I MUST use GRUB, I don't know how to make the menu.lst options correspond to syslinux.cfg, since they're not in the same format.  I need things like "append file=/preseed/ubuntu.seed boot=casper persistent" etc in the menu.lst file for GRUB, but I'm not sure how to do it.

Another (simpler for me) solution would be to use GRUB and somehow transfer boot control to syslinux when it gets to /dev/sda2.  Any help would be much appreciated.  Thanks!

EDIT: Nevermind, I used install-mbr (Debian package 'mbr') to do it.  Invoking "install-mbr /dev/sdb -d 2" did the trick, by setting the default partition to boot number 2. (and putting syslinux on the boot sector of /dev/sdb2, the 2nd partition).

Now, though, I'm unable to start X using the LiveUSB stick (it worked once on my desktop, now it won't work on my laptop).  I get an "unable to lock ~/.ICE-authority" error of some sort.  Something about their being no free space or an installation error.  Oh well, here we go again.

---

