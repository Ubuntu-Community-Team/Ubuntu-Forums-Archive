---
title: "Gnu Grub Version 2.04"
date: 2021-11-25
forum: General Help
---

### Post by NDW57 on 2021-11-25
Hi, I recently tried to install Xubuntu (20.04 I think) "over" MX Linux by deleting/overwriting the latter. I created a USB stick using the burner on MX-Linux and before I did this I checked the downloaded xubuntu iso with the SHASUM "thing" and all seemed well. I managed to get into the boot menu eventually by pressing F12 and was able to access the stick and commenced the installation process. It seemed to go well and Xubuntu seemed to be working. However when I rebooted I got the screen entitled Gnu Grub Version 2.04 "Minimal BASH-like line editing is supported.For the first word, TAB lists possible command completions.Anywhere else TAB lists possible device or file completions" Below that is displayed "grub>(flashing cursor)". All the advice I have seen suggests things like CTRL/ALT/DEL then "hammering" the key (F12 for me) to access the boot menu. I have tried this with absolutely no success. Indeed, all of the advice I have found seems to be centred around accessing the boot menu and I am simply unable to do this. Any thoughts? Is it new PC time? Incidentally I am currently using a half decent laptop rather than a mobile or tablet so I CAN access the internet properly and download stuff and make USB sticks and the like if that helps.

---

### Post by oldfred on 2021-11-25
It sounds like Xubuntu's grub did not install, and you are booting with the old grub you had.
Did you install in same boot mode as previous install, or were both UEFI or both BIOS.
And then in UEFI/BIOS is system set to boot in that mode?

If UEFI fast boot on, you often do not have time to press any key when booting. 
You then can do a full power down or "cold" boot. If laptop also remove battery and hold power switch for 10 sec or so, so all power is drained. 
Then it should do normal boot one time, but give you time to press correct key to get into UEFI to turn fast boot off.

From grub> you may be able to manually boot.


If install is in (hd0,1)/ sda1 or change to where your install is:
grub> ls
grub> ls (hd0,1)/
grub> set root=(hd0,1)
grub> linux /boot/vmlinuz root=/dev/sda1
grub> initrd /boot/initrd.img
grub> boot

---

### Post by NDW57 on 2021-11-25
Just tried that. The install appears to be in (hd1,msdos5) - at least that shows activity at the correct time when I tried to install Xubuntu. So I tried the set root=(hd1,msdos5) command and got "error: not an assignment". The computer works on UEFI if that helps and I always go for the default mode when doing an install.

---

### Post by yancek on 2021-11-25
Your last post indicates you have 2 drives and you refer to MX Linux And Xubuntu.  So if I understand, you want only Xubuntu installed and no other OS on either/any drive, correct?
Your last post indicates your machine uses UEFI, was MX installed UEFI?  If so, you should already have an UEFI partition.  Did you boot and install Xubuntu in UEFI mode?  You also indicate by the boot set root entry that it is an msdos machine, using the older Legacy/CSM boot method.

Run the live Xubuntu and from a terminal run the following commands and post the output here so other members can see:

> sudo fdisk -l
sudo parted -l

Lower case Letter L in both commands to list the partition information.

---

