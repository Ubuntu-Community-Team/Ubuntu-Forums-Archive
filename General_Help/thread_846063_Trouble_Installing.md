---
title: "Trouble Installing"
date: 2008-07-01
forum: General Help
---

### Post by BiggieD on 2008-07-01
Hi. I'm using a Acer Aspire 5100 with a 160GB NTFS ATA HDD (running Vista).
My problem is that I am not getting any option to install Ubuntu on a seperate partion. I only have the guided option to do a full install deleting everything on my drive.

I have looked at the manual settings and notice that I seem to have 3 partions (why I have 3 is news to me as Vista only shows me my C drive and backup drive partions in "My Computer").

If anyone could help, I'd much appriciate it.

Many thanks.

---

### Post by BiggieD on 2008-07-01
Please help

---

### Post by adam_kimber on 2008-07-01
ALl propritary laptops, such as Dell, Acer etc have at least two partitions. The first is the day to day C: drive in windows and the second contains certain manufacturer's information. Third partitions are sometimes "user files" or backup or whatever. If you are not using that partition you can use that for Linux/Ubuntu. 

However if you are using both partitions then you have a problem. It is this, the physical disk has been divided into 3 and then formatted. This means there is no "free" unformatted space for you to put Ubuntu on. To do this you will have to either resize a partition using gparted [Gparted live CD]("http://gparted.sourceforge.net/livecd.php"), which if it goes wrong can lead to total loss of data, or formatting the entire disk and writing out as many partitions as you need for both linux and windows, which also leads in loss of data. 

Have a look at [this guide]("http://www.psychocats.net/ubuntu/installing")  for installing Ubutnu on a dual boot machine. Not sure if its up-to-date for the latest version of ubuntu though..... 

Check out the option for Guided resize and use freed space as that might be the one you need.

---

### Post by plucky on 2008-07-01
> **BiggieD said:**
> Please help

Use the Vista disk management to shrink a partition to leave the amount of space you want for Ubuntu.Leave the space gained as unallocated. When it comes to the partitioning stage,get it to use the unallocated space.


See this link [Pyschocats Installing](http://www.psychocats.net/ubuntu/installing) for more information.

You are allowed a maximum of 4 primary partitions,so your last partition will have to be an extended partition into which you can place as many partitions as you wish.You could just let the installer install a root or / and a swap partition,or you can have a separate home partition as well.You can choose at installation time.Linux allows you to boot an extended partition.

Good Luck.

Please do no bump your thread so soon,it is considered impolite.

---

### Post by BiggieD on 2008-07-01
Thanks for the help guys. I will check out the solutions given. And sorry for the quick bump. Won't do that again.

---

