---
title: "I hate grub2"
date: 2014-07-21
forum: General Help
---

### Post by jason116 on 2014-07-21
Hello,

I recently started trying to setup an htpc. I went with xbmc with Ubuntu. However I'm having trouble setting up a software raid 1. I've tried following multiple guides, with no avail.
I don't know why you can't create a software raid during the install. I've booted via the live cd and have tried creating the raid prior with mdadm but with no luck using the guides
I've found. 

I've been attempting to follow this guide [https://wiki.archlinux.org/index.php/Convert_a_single_drive_system_to_RAID](https://wiki.archlinux.org/index.php/Convert_a_single_drive_system_to_RAID) but dealing with grub2 seems to be a nightmare. I've tried using boot-repair
and still can't get a bootable system. I even uninstalled grub2 and attempted to install grub. 

Any help would be much appreciated.

---

### Post by grahammechanical on 2014-07-21
I love Grub 2.0. I have just put in an install of Ubuntu 12.04.4 and that uses Grub 1.99. What a difficult to use Grub menu!. I have several installations of Ubuntu and its flavours and they all have more than one Linux kernel. So, the Grub 1.99 menu gets so complicated as to be unusable. But with Grub 2.0 All those previous kernels are in the Advanced Options sub-menu and each installation is clearly labelled with the partition name that it is on. Much more usable.

What is Grub doing wrong? What exactly is the problem? Where is the link to the pastebin site with the Boot Repair report?

Regards.

---

### Post by oldfred on 2014-07-21
The desktop installer does not directly support RAID. It used to be with 12.04 that you had to use the Alternative installer, but that was eliminated and the said they would add RAID & LVM type installs to desktop. They seem to have added LVM, but not all of RAID works.

 Elimination of Alternative installer for 12.10 and no RAID support directly for Desktop.
[http://ubuntuforums.org/showthread.php?t=2049021](http://ubuntuforums.org/showthread.php?t=2049021)

---

### Post by jason116 on 2014-07-22
I think my problem is that I can't boot using the raid after I create it.

[http://sysadmin.compxtreme.ro/how-to-migrate-a-single-disk-linux-system-to-software-raid1/](http://sysadmin.compxtreme.ro/how-to-migrate-a-single-disk-linux-system-to-software-raid1/)

I keep getting dumped to the initramfs prompt where I can't do anything. 
For whatever reason it can't find /dev/md0

---

### Post by oldfred on 2014-07-22
Is this an UEFI system.
Often with RAID, you have to add or edit the grub.cfg in the efi partition with a configfile entry to the grub.cfg in your md partition.

This is not a RAID version, but same idea, grub in efi only needs this:
 configfile (hd0,gpt8)/boot/grub/grub.cfg

 grub.cfg into /EFI/ubuntu works, even when grubx64.efi is in /EFI/Boot

      
 grub doesn't boot with efi and md raid root
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229738](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229738)
RAID install with efi, need configfile and grub in efi partition.
[http://ubuntuforums.org/showthread.php?t=2190716](http://ubuntuforums.org/showthread.php?t=2190716)
[http://askubuntu.com/questions/355727/how-to-install-ubuntu-server-with-uefi-and-raid1-lvm](http://askubuntu.com/questions/355727/how-to-install-ubuntu-server-with-uefi-and-raid1-lvm)

---

