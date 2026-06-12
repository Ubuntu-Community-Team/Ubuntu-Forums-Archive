---
title: "Dual boot install, can't boot Win 7"
date: 2016-06-26
forum: General Help
---

### Post by J_Harp on 2016-06-26
Asus K54L, 64 bit Windows 7, Memory 3.8 GiB, Intel® Pentium(R) CPU B950 @ 2.10GHz × 2, Graphics Intel® Sandybridge Mobile, Disk 40.2 GB

I installed 14.04 as dual boot, I can only boot Ubuntu, if I click EFI/ubuntu/MokManager.efi it goes into a loop wanting input for the Mok operation. I tried to attach a picture of the power-up screen but it has disappeared.

Here is the URL I got when I ran Boot Repair.   [http://paste.ubuntu.com/17831517/](http://paste.ubuntu.com/17831517/)

I posted the URL to [email]boot.repair@gmail.com[/email] but haven't heard from them. Thank you for any help.

Jim

---

### Post by yancek on 2016-06-26
I don't know how you managed it but there is no sign of windows on that machine other than the efi files on sda3.  Did you select the option to Erase disk and install Ubuntu?  You might be able to save some data from the disk from windows by using testdisk but I expect if you want windows you will have to reinstall it.  No recovery partition.

---

### Post by J_Harp on 2016-06-26
I choose do something else, and thought I had followed the instructions step by step to install it as dual boot, but obviously went astray somewhere. 

I have an unopened Win 7 disk which I purchased from my ISP and never used. Trouble with that is I don't know if Microsoft would activate it since it is marked for installation on a new machine.

Loss of Windows doesn't bother me a bit, I only wanted to keep it because this was my wife's former computer, and there was still some of her stuff on it. We have offsite backup, and if we transfer that account to her Win 10 machine all should be good. Thank you for the reply.

---

### Post by yancek on 2016-06-26
Did you shrink your windows partition from Disk Management in windows to create unallocated space before trying to install Ubuntu?  Your Linux partitions are using the entire drive.  Generally, you will need free space on which to install and you can't install Linux on a windows partition with a windows filesystem (ntfs).  Well, you can, it just won't work.  If you do an install again, make sure you have free space by shrinking windows partitions first.   Glad you have backups.

---

### Post by J_Harp on 2016-06-26
Yes, shrank partition in windows disk mgmt, then created partition table. I just made two partitions, boot and swap I think they were called, didn't create a home partition. Made the swap partition 9.2 GB, don't remember the size of the other one, and I'm not sure of the name of it.

I just read on another thread that I should have used a new ISO of 14.04 on the usb flash drive, the one I used was about a year old, and that may be the problem as there was a bug mentioned which would wipe the whole disk. Here is a link to that thread.

[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

I won't be available to respond til sometime tomorrow  afternoon, medical tests scheduled. Thank you for your interest.

---

### Post by Bucky Ball on 2016-06-27
Yep, bad news is Win is gone. Good news is Ubuntu is installed and booting perfectly by the sounds of it! :)

Please mark the thread as solved to help others if you need no more help with this. Thanks.

---

