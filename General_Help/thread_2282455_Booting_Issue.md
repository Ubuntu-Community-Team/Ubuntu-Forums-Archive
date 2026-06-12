---
title: "Booting Issue"
date: 2015-06-14
forum: General Help
---

### Post by i-john-m on 2015-06-14
Just a couple probably simple questions:

First, I'm running Ubuntu 15.04 on a HP Pavillion All-In-One 23.  Machine boots fine, except for one small detail---on startup, my monitor is blank (I know the OS is booting fine because I hear the "conga" tone on startup).  Takes about 3 times of power off/power on to finally get a display...Any ideas?

Second, GRUB still shows Windows Boot Loader (whatever it is) on dev/sda1, even though this is a standalone Ubuntu install (no Windows whatsoever).  How do I fix this?  update GRUB or whatever?  How do I do that?

Thanks for all your help!
JT

---

### Post by Steve_Horan on 2015-06-14
Couple things. Once you are logged in try to correct lightdm.

> dpkg-reconfigure lightdm

Also attach **/var/log/boot.log** so we can inspect this for errors. When the display manager in black are you about to enter any of the tty terminals? (CTRL + ALT + F1)

Also provide the output of fdisk -l. Lets make sure your windows partitions are removed before correcting grub.

---

### Post by dino99 on 2015-06-14
for your first question/issue, its a graphic driver installation issue. Let us know which card/chipset is inside, and which driver has been installed (check activation via 'additional drivers') (from software-properties)

the second request is more confused: if that Pavillion onlu has ubuntu installed, then the grub menu cant show 'windows' (you might hold a ghost there ;) )

Please post the output of:  > sudo blkid

Then grub should have been installed on /dev/sda , not sda1. Purge it first then reinstall it:
> sudo apt-get purge grub*
sudo grub-install /dev/sda

and reboot

---

### Post by wildmanne39 on 2015-06-14
I changed the title of your thread to make it more descriptive of the issue you are having, this helps to get your question answered.

---

### Post by yancek on 2015-06-14
The first problem could just be the graphics driver as suggested above.  I had a similar problem when I first installed 14.04.  Every time I booted I got a garbled screen and had to manually power off.  When I rebooted, I got the Desktop.

Did your computer come with some version of windows pre-installed or did you install windows and then Ubuntu over it?  If you had windows, which version?  How new is the computer and does it have UEFI?

---

### Post by i-john-m on 2015-06-14
Thanks, guys.
Here is some of the requested output---first, from sudo blkid:

/dev/sda1: UUID="37A9-8ABF" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="04c90815-3ea4-42c6-a589-c618d1125fdc"
/dev/sda2: UUID="fee7be9e-1d36-4131-bff5-9fe229bd2042" TYPE="ext2" PARTUUID="62e45b9f-c52a-486a-9436-8101c62b599b"
/dev/sda3: UUID="d38jl3-gnzk-toCP-zs0w-P426-ie3q-oRZnXL" TYPE="LVM2_member" PARTUUID="5d44c5cb-bdcd-492d-96c5-eee742f8e4f6"
/dev/mapper/ubuntu--vg-root: UUID="3ad3a5d1-b775-4613-a969-95b2709b6ce0" TYPE="ext4"
/dev/mapper/ubuntu--vg-swap_1: UUID="8ae1eac7-6c0e-4222-bf38-350e954ed29a" TYPE="swap"


Chipset/graphics controller:  AMD A6-5200 APU with Radeon(TM) HD Graphics
further:  Radeon HD 8400 / R3 Series

Output of fdisk -l:  Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: E6B1EDDD-1D36-42E1-830F-C9F8C21C09C9

Device       Start        End    Sectors   Size Type
/dev/sda1     2048    1050623    1048576   512M EFI System
/dev/sda2  1050624    1550335     499712   244M Linux filesystem
/dev/sda3  1550336 1953523711 1951973376 930.8G Linux LVM

Disk /dev/mapper/ubuntu--vg-root: 927.3 GiB, 995685826560 bytes, 1944698880 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk /dev/mapper/ubuntu--vg-swap_1: 3.5 GiB, 3711959040 bytes, 7249920 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

This PC originally had Win8.1 installed.  I tired installing Ubuntu 14.04 as a dual-boot, but because of the whole UEFI thing, I gave up.  When 15.04 came out (and presumably, the UEFI bugs were fixed), I installed it again as dual, then went back and installed it as standalone.  
It should be noted that I'm still running the PC with SecureBoot disabled---would this cause these foul-ups?
Anyway, hope I didn't miss anything.
JT

---

### Post by i-john-m on 2015-06-14
> **Steve_Horan said:**
> When the display manager in black are you about to enter any of the tty terminals? (CTRL + ALT + F1)


Nope, unable to see anything but a black screen.

---

### Post by yancek on 2015-06-14
You have an EFI partition (sda1) which might be why you see a reference to windows.  You have also installed using LVM which I have never used.  While you are waiting for a response from someone with experience with EFI and LVM, you might go to the site below and download and run the boot repair iso, selecting the option to Create BootInfo summary.  Did you install Ubuntu in UEFI mode?


 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by i-john-m on 2015-06-14
> **dino99 said:**
>  Let us know which card/chipset is inside, and which driver has been installed (check activation via 'additional drivers') (from software-properties)




I'm sorry---total n00b here---how do I get to that?  sudo software-properties?

---

### Post by oldfred on 2015-06-14
It looks like you have installed with LVM or LVM with full drive encryption.

The efi partition sda1 probably still has a /EFI/Microsoft folder. That has the Windows efi boot files which without Windows do not mean anything. You can delete that folder, but do not delete /EFI/ubuntu  folder as that has the grub boot files.

You also probably have UEFI settings it has saved in NVRAM. You can also remove those with efibootmgr.

       sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). 
Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

