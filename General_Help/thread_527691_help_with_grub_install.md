---
title: "help with grub install"
date: 2007-08-16
forum: General Help
---

### Post by Naegling23 on 2007-08-16
Ok, so here is my issue:

I am trying to remove a 10gb hard drive from my system.  When I remove it, I get a grub error: OS not found.  I didnt think that I installed grub to that drive, but...it looks like I did (or is this error something else?).  Anyway, how can I install grub to another drive so that I can remove the 10gb one.  I have a completely working system, so I would like to install grub on one of the drives Im keeping, then pull the 10gb one out.

---

### Post by Herman on 2007-08-17
Hello Naegling23,
As you might already know, or maybe not, boot loaders come in two or three separate pieces. 
The first part of a boot loader, called 'stage1', is very small, in order to fit inside a 446 byte area in the Master Boot Record reserved for boot loader code.  The 'stage1' part of a bootloader is really not much more than a pointer, to make the Master Boot  Record point to a partition on the hard disk.

Inside the partition there could be a boot  sector at the start of the  partition that contains more boot loader files, and then there will be more boot loader files somewhere that do the actual work of loading an operating system's kernel. That part of a boot loader is often called 'stage2', and would be much larger than any other part of a boot loader.

All hard disks have a Master Boot Record once they have been formatted.
You can install the stage 1 for  a boot loader to any MBR, but the BIOS will only normally look in the MBR of the first hard drive. > I am trying to remove a 10gb hard drive from my system. When I remove it, I get a grub error: OS not found. I didnt think that I installed grub to that drive, but...it looks like I did (or is this error something else?).
 It is something else, 'Operating System not found' is not a GRUB error, but probably an error message from your BIOS, meaning the hard disk you are trying to boot has not yet had a boot loader's stage1 file written to it, or it has no 55aa bootable disk signature, or it doesn't have a boot flag. That means you probably have GRUB's Stage1 file in the MBR of the 10 GB hard disk you are removing, but the matching GRUB stage2 files that it looks for are possibly in another hard disk, that still might be in your computer, but that simply  doesn't have a MBR pointing to it.> Anyway, how can I install grub to another drive so that I can remove the 10gb one. I have a completely working system, so I would like to install grub on one of the drives Im keeping, then pull the 10gb one out.There are lots of ways to install the stage1 code from GRUB to MBR on a hard disk. Probably the fastest, easiest and most reliable would be to use [Super Grub Disk]("http://geocities.com/supergrubdisk/") to do that with.

Otherwise if you can boot Ubuntu while the 10.0 GB hard disk is still in your computer you can install GRUB to MBR of whichever will be your first hard disk after the 10.0 GB one is gone and then you should be able to boot when the 10.0 GB is removed. Here is a link about how to do that, [                                                                  Re-install GRUB with a GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD") that will also work with the Ubuntu Live CD even if you don't have your 10.0 GB hard disk in and your computer won't boot from hard disk.

You may need to edit your /boot/grub/menu.lst file too, if your 10.0 GB hard drive was your first hard disk, (by the sounds of things that's most likely), then your hard disk number for Ubuntu might  be changed. Here's a link about how to access your hard disk installed Ubuntu from a Live CD and open the bootloader files from the LiveCD in case you end up needing to do that, it's not too difficult at all, [                                  Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") rescue your Linux system with a Live CD.

I hope something there helps,
Regards, Herman :)

---

