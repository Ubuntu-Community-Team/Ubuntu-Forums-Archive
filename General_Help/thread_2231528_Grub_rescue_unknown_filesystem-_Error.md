---
title: "Grub rescue: unknown filesystem- Error"
date: 2014-06-26
forum: General Help
---

### Post by boris6 on 2014-06-26
I've already researched the subject, and i already fixed the problem on my computer by using boot repair - [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


But now i have the same problem with my other computer, the problem is i'm not seing all the options in Boot-Repair's menu, i only see the "create boot info summary" and nothing else(not even the advanced options). 
On my other computer, all i had to do is click "Recommended repair" and it was fixed. 


I did run the symmary and these are the results - [http://paste.ubuntu.com/7705081/](http://paste.ubuntu.com/7705081/)

Any suggestions on how to fix this?

---

### Post by yancek on 2014-06-26
What exactly are you trying to do?  The info you posted shows Grub installed on the master boot record of the 640GB hard drive and only one partition on that drive, sda1 which is a windows partition.  Since most Grub files are on the / partition of the Linux distribution, you don't have the Grub files necessary to boot.

> Any suggestions on how to fix this? 		

Boot windows, defragment the windows partition, shrink the partition to make room to install a Linux distribution to use Grub.

---

### Post by boris6 on 2014-06-26
You're right - i have one hard drive in two partitions. I used to use win 8 and had 2 partitions but when i installed mint (i chose the options where it replaces windows) it merged them together and deleted all my files. I used testdisk to recover them(which worked), i restarted and now i get this error and can't log back in.

Of course i want to avoid formating the drive because i don't want to lose my data again.

All i want to do is access my files again so i can tranfser them someplace safe. Any ideas on how to do that?

---

### Post by yancek on 2014-06-26
> You're right - i have one hard drive in two partitions

The info you posted shows you have one hard drive with one partition and that partition is a windows partition.  You also have the 4GB flash drive showing.   There is nothing showing in that report that you have any Linux filesystem or partition.  Are you referring to data on the installed windows 8?   Did you reinstall windows 8 after your earlier problem?  You don't have any Linux partitions so obviously you can't boot Mint.  What are your intentions?  Do you just want windows 8?  Do you want to boot both Mint and windows 8?

---

### Post by boris6 on 2014-06-27
I wanted to replace Win 8 with Mint entirely, so installed it, it successfully booted and everything was fine. I guess my mistake was not to format the partition, i just didn't know that would be a problem. I made a new partition (ext4) and now it works fine.

---

### Post by yancek on 2014-06-27
Glad to see you got it working and yes, doing a new install on unallocated or free space or a non-Linux partition does require formatting.

---

