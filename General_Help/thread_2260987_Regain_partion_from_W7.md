---
title: "Regain partion from W7"
date: 2015-01-15
forum: General Help
---

### Post by Les_Fairlie on 2015-01-15
Hello Ubuntu

Several years ago I installed Ubuntu and duel booted with XP. For reason I can no longer remember I uninstalled Ubuntu so I could just run XP. However I wasn't able to regain the partition so I just ran XP in the smaller one.
I now have W7 x64 on a PC I got about six years ago and I am thinking of installing Ubuntu again and dual booting for a while until I am ok with it and then uninstalling W7.
Before I do it I want to know if I will be able to regain the W7 partition space.
I have read about UEFI and, please correct me if I have understood it incorrectly. but I think that I should be able to change my W7 to that format, then install ubuntu, and if I wanted to in future, be able to uninstall W7 and regain its partition space.

Thanks

---

### Post by yancek on 2015-01-15
If you install Ubuntu in a dual boot with windows 7 and then decide you longer need or want windows 7, you can use a partition editor in Ubuntu (usually GParted) to format the windows 7 partition(s) in a Linux filesystem format and use on Ubuntu.

You will need to check the BIOS on boot first to see if your computer has UEFI capability.  There should be a fairly obvious option.

---

### Post by Les_Fairlie on 2015-01-15
Thanks for your reply. I have one more question.
If I wanted to uninstall ubuntu and go back to W7 would I be able reclaim that partition?

---

### Post by yancek on 2015-01-15
> I have read about UEFI and, please correct me if I have understood it  incorrectly. but I think that I should be able to change my W7 to that  format,

Just to clarify, UEFI is just a new method of booting operating systems which have been using the MBR (master boot record) method for about 35 years.  In the future I'm sure all computers will use UEFI.  You do need to verify that your hardware is capable of UEFI, probably is with windows 7, but you need to check.

> If I wanted to uninstall ubuntu and go back to W7 would I be able reclaim that partition? 		 

Another clarification, you don't uninstall operating systems the way you do applications on the system.  Works the same for windows, Linux or any other system.  The basic method is to format the partition during the install.  A standard windows install will generally overwrite any non windows systems or partitions during an install.  Ubuntu has this as an option and you are asked if you want to do an ERASE DISK and install Ubuntu.  So to answer your question, yes.

---

### Post by yancek on 2015-01-15
Deleted duplicate post.

---

### Post by Les_Fairlie on 2015-01-16
Thanks for your help

---

