---
title: "Wipe HDD except OS boot"
date: 2021-11-19
forum: General Help
---

### Post by roberteadie on 2021-11-19
Hi, I'm a relative newcomer to Ubuntu, and have been experimenting with Docker and WebODM.  Often, I push things to the limit, and want to 'clean up' as much as possible.
Till now I've reinstalled Ubuntu 20.04 (I think) from USB, then reinstalled docker and WebODM, which is all quite quick.  HOWEVER this requires a screen and KBD/Mouse, and I have now moved the computer to a remote location without easy access, and am wondering how easily I can wipe everything EXCEPT Ubuntu remotely using an SSH connection + commands?  Clearly I want to keep SSH and my user login, but am happy to do everything else via SSH.
(Using lsblk + options I cna see I have 3 devices
sda1 1MB
sda2 ext4 1GB /boot
sda3 LVM2_member 231GB 
and under sda3 ubuntu--vg-Ubuntu--lv ext4 115GB /

231GB is the whole HDD, so I'm not sure what is the 115GB (half the HDD?)

I was hoping to be able to just wipe something, and be able to start with a clean ubuntu again?

Thanks for any help.  Robert

---

### Post by yancek on 2021-11-19
>   
(Using lsblk + options I cna see I have 3 devices

No, the output you show from lsblkd below:

>  sda1 1MB
sda2 ext4 1GB /boot
sda3 LVM2_member 231GB 
and under sda3 ubuntu--vg-Ubuntu--lv ext4 115GB /

shows you have three (3) partitions on one physical drive.  The sda part refers to the drive, the numbers after the sda refer to the partitions on the drive and the part "under sda3" indicates that you have done an LVM install which I have never done and can't help with.  THe sda1 looks like it could be a bios-grub (1MB) partition for a Legacy/CSM install on a GPT drive, then the separate boot partition (which I think is needed with LVM and sda3 is the LVM partition which contains the OS and your data.  I'm not sure about the difference between the drive seze 231 and the vg-Ubuntu size 115GB as I don't know LVM.  Take a look at the link below as it may be helpful..

[https://www.howtogeek.com/211937/how-to-use-lvm-on-ubuntu-for-easy-partition-resizing-and-snapshots/](https://www.howtogeek.com/211937/how-to-use-lvm-on-ubuntu-for-easy-partition-resizing-and-snapshots/)

---

