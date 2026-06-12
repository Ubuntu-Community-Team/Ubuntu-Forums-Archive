---
title: "New to Ubuntu, C: and D: not visible"
date: 2013-02-07
forum: General Help
---

### Post by brendanjr on 2013-02-07
Hi to all,
 
Last week my Windows Vista decided to stop working. I have gone through many forums and tried different things to restore it, however the Windows files seem to be corrupted and I cant restore anything.
 
I am trying atm to backup files from the C: and D: partitions by using Ubuntu 10.11 which I am currently running off a USB stick. I have noticed when trying to install Ubuntu that my d: and c: partitions are named /dev/sda2 and /dev/sda3, while the partition with the recovery files for Windows is called /dev/sda1.
 
The only problem is when I try to access the Windows partitions through the Computer folder in Ubuntu, and none of the partitions show up, which is making it hard for me to copy files off these partitions.
 
Can anyone suggest what I should do to access these partitions through Ubuntu?
Please take into consideration that I am a complete newbie when it comes to working with Linux.
 
Any help will be most appreciated, thanks.

---

### Post by ryan27968 on 2013-02-07
run this code in terminal without the quotes: "sudo fdisk -l" and give back the results. oh and also... what is the size of your drive partitions respectively and what is the size of your flash that you are booting off?

---

### Post by claracc on 2013-02-07
what ubuntu release are you using?, ubuntu 10.11 doesn't exist.

Here: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows), there is a link to mount your windows partitions when you run ubuntu. In this way, you will be able to backup them. But as you can see, the procedure depends on what ubuntu you are using.

---

### Post by grahammechanical on 2013-02-07
>  when I try to access the Windows partitions through the Computer folder in Ubuntu, and none of the partitions show up, 

The computer folder is Ubuntu. You should be seeing partitions in the left panel of the File Manager. They might be called File Systems. But if you are using 12.10 they may show as volumes under Devices. It is difficult to help you without knowing what version you are Using.

---

