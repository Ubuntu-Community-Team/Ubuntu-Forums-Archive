---
title: "Installed Ubuntu on usb, now Windows XP won't boot"
date: 2013-05-05
forum: General Help
---

### Post by KuroOu on 2013-05-05
I used Lili to make a live usb for ubuntu. After, Iused the boot menu to boot the usb. I used that to install ubuntu to another usb. I restarted my pc and the grub menu comes up showing that I can boot Ubuntu, Ubuntu in safe mode, and  Windows XP Pro. Ubuntu boots fine but whenever I try to boot windows it shows this:

"SYSLINUX 4.06 EDD 2012-10-23 COPYRIGHT (C) 1994-2012 H. Peter Anvin et al
No child node, aborting...
No child node, aborting...
ERROR: No configuration file found
boot:          "

I pressed "e" to edit the Windows XP Pro entry, it showd this:

"setparams 'Microsoft Windows XP Professinal ( on /dev/sda1)

insmod part_msdos
insmod ntfs
set root=(hd0,msdos)
search --no floppy --fs-uuid --set=root 9C90C26290C2428E
drivemap -s (hd0) ${root}
chainloader +1"

Is there something I need to do or change to get windows to boot?

---

### Post by oldfred on 2013-05-05
It seems like it is trying to boot the flash drive installer not Windows?

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by KuroOu on 2013-05-05
I'm downloading the iso for boot repair and i'll report back as soon as I can.

---

### Post by KuroOu on 2013-05-06
My pc doesn't have an internet connection so I'll upload the boot info file.
Had to use a file host, forum wouldn't let me use it as an attachment. [HTML]http://filecloud.io/vq389uxh[/HTML]

---

### Post by oldfred on 2013-05-06
I cannot get to that site without signing up. 

You also had this:
set root=(hd0,msdos)

You are missing the partition number.
set root=(hd0,msdos[COLOR=#ff0000]1[/COLOR])

---

### Post by KuroOu on 2013-05-06
Here, I uploaded it to mediafire. You can view it instead of downloading it. [http://www.mediafire.com/file/pqz4dphqcka1ty6/Boot-Info_2013-05-05__16h30.txt](http://www.mediafire.com/file/pqz4dphqcka1ty6/Boot-Info_2013-05-05__16h30.txt)

---

### Post by oldfred on 2013-05-06
You installed syslinux to the Widows NTFS PBR - partition boot sector. That has to have Windows in it as that is how Windows boots. If only installed once, NTFS has a backup and that can easily be restored with testdisk.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR similar instructions:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

It looks like you install Ubuntu to sdb, but have a large FAT32 partition. My install to my 16GB flash drive used 8GB for / (root) and 8GB for data.

---

### Post by KuroOu on 2013-05-06
Alright, I'll try this and let you know what happens.

Using testdisk worked like a charm. Thank you very much.

---

