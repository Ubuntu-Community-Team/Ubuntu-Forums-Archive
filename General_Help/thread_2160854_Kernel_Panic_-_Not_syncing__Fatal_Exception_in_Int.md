---
title: "Kernel Panic - Not syncing : Fatal Exception in Interrupt"
date: 2013-07-08
forum: General Help
---

### Post by samyakd on 2013-07-08
Right from the very beginning, I have a new UEFI pre-installed Windows 8 system on which I installed a dual boot 64-bit Ubuntu 12.04.2 LTS. It was working fine except today when more than twice, my system crashed with a black screen showing the following message at the end : "Kernel Panic - Not Syncing : Fatal exception in Interrupt". I googled this and got to no particular solution. After two such crashes, I copied the log file in dmesg.0 into these two paste URLs : 
1. [http://paste.ubuntu.com/5855604/](http://paste.ubuntu.com/5855604/)
2. [http://paste.ubuntu.com/5855647/](http://paste.ubuntu.com/5855647/)
These two have separate log files of separate crashed sessions. Also, if its relevant here, I have a RaLink wireless adapter for which I had to manually install its driver.

Also, there is this bug report from which I couldnt make out anything.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1181392](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1181392)

Edit : Also, it might be a problem with wireless because I am using this on lan for the last 90 minutes or so without any fault. Please help.!!

---

### Post by dino99 on 2013-07-08
is it reproducible when using an older kernel ?  are you using some bleeding edge packages from ppas ?
a fsck might let you know about possible partitions issues; and memtest have to be ran too.

---

### Post by samyakd on 2013-07-12
Bleeding edge : Yes, i guess. To make this new UEFI enabled laptop to dual boot I had to install a package named boot-repair. The package is here  : [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Also, about older kernels. I presently use 3.5.0-36. I booted with 3.5.0-23 and reinstalled the wireless driver for that kernel. And yes the kernel did panic.! :(

---

### Post by slgtheindividual on 2013-10-01
I've been having the same issue with a very similar situation, I had to use boot repair to fix boot problems associated with a new laptop with UEFI.

---

### Post by slgtheindividual on 2013-10-01
so I read the bug report here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1181392](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1181392)

which suggests a solution; install firmware-b43-lpphy-installer 

run in a terminal (ctrl+alt+t)
sudo apt-ge[SIZE=2][FONT=arial]t install [COLOR=#333333]firmware-[/COLOR][COLOR=#333333]b43-lpphy-[/COLOR][COLOR=#333333]installer

I have since done this and have no longer experienced the issue, I suggest the author of this thread try this and if it works mark the thread solved.
Hope this helps. [/COLOR][/FONT][/SIZE]

---

