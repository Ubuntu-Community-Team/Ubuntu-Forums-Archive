---
title: "GRUB 1.99 vs GRUB 2.0 - problem with entries"
date: 2012-10-22
forum: General Help
---

### Post by amjjawad on 2012-10-22
Hi,

I'm sure most know about this. I had posted previously at Ubuntu+1 section but that is closed so this is a new thread.

This is the result of the boot info script: [http://paste.ubuntu.com/1296827/](http://paste.ubuntu.com/1296827/)

Lubuntu 12.04 i686 is my main system
Lubuntu 12.10 i686 and Lubuntu 12.10 amd64 are installed on /sda7 and /sda8.

GRUB1.99 is taking the control, obviously since Lubuntu 12.04 is the main system.

How can I get rid of the long entries? I'm afraid if I use GRUB Customizer, it will create more problems. It did before even without GRUB2.0 is being installed now that I have both GRUB versions, I guess I will not use GC.

Thanks!

P.S.
I know I can install GRUB2.0 to the MBR but I don't want that. I still want to use GRUB1.99

---

### Post by oldfred on 2012-10-22
HI, amjjawad

When you have multiple installs, you can boot into any of them and directly install grub to the MBR and then that install is the first in the grub menu & the one in control.

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

A more complete reinstall is better if you have multiple drives as grub remembers where to reinstall, and if installed to another drive or  a partition may try to reinstall to that on major updates.
#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

I followed directions from drs305 and Ranchhand to customize my grub menu. And I turn off os-prober and use 40_custom for just about everything. Cavsfan has documented that process or you can go back to some of the old threads.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Older thread
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

---

### Post by amjjawad on 2013-09-20
Although I did not find a way to fix this issue nor I do have time even to look for that but I will mark this thread as solved for now.

I am sorry if someone with the same Q will be directed to here from Google but he/she can start a new thread if he/she is interested.

Thank you!

---

