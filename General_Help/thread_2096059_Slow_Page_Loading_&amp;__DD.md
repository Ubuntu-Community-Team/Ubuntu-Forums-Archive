---
title: "Slow Page Loading &amp;  DD"
date: 2012-12-18
forum: General Help
---

### Post by Mike Green9 on 2012-12-18
Hi.

I am having a blast with my recently installed Ubuntu 12.1. I have a dual boot setup - W7 & Ubuntu, each in their own 25 gb partition. I also set up a 2gb swap partition for Ubuntu. I set swappiness to 10.

I have 3 questions:

1. Under Ubuntu, web page loading is very very slow. Under W7, pages load rapidly. Are there some parameters that I can play with to improve throughput?

2. I have 2 drives on the system. The second drive is used only as a backup to the first. I used dd to make a backup of Ubuntu:  sudo dd if=/dev/sda4 of=/dev/sdb4 bs=2048
This took approx 15 minutes, and seemed to work fine. I then booted off the backup drive (sdb) and chose to invoke Ubuntu which resides on sdb4. Can terminal tell me which drive I am in. PWD shows me the working directory, but how can I display the drive/partition i.e. sdb4 ? Ideally I would be able to display the FULL path, including the drive.

3. I use 'sudo dd if=/dev/sda4 of=/dev/sdb4 bs=2048' just in case Drive 1 gets clobbered. In that case, I would be able to boot off the second and run W7 or Ubuntu as always. Can I improve the copy time with a large bs? Should I use conv=sync?

Thanks for your help,

M....

---

### Post by Mike Green9 on 2012-12-21
Bump.


M....

---

