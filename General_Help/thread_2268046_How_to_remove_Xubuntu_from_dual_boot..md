---
title: "How to remove Xubuntu from dual boot."
date: 2015-03-05
forum: General Help
---

### Post by gordon99 on 2015-03-05
My HP Compaq Presario56 came with Windows 7 installed. I re-partioned the HDD and added Xubuntu some month ago.  Recently, I reinstalled Xubuntu and although I do not know if there is any connection with this operation I now find  that when I suspend Xubuntu, or put Windows into sleep mode, neither system will wake up unless I switch off and re-boot. Also neither will go into sleep mode if I shut the lid. As I say, I am not sure if the re-installation of Xubuntu is the cause of the problem because I cannot be sure if the fault immediately followed the re-installation.

I have tried various "cures" that I have read involving graphics card drivers without success. 

I started a new thread here a few days ago, specifically about the sleep mode problem, where I  requested help but have had no response so far. I therefore think my best option at this point is to remove Xubuntu on a temporary basis, leaving Windows 7, in order to test if it is the Xubuntu install which has caused the problem.  I would like to leave the Windows partitions as they are so that I can re-install Xubuntu later.  Can someone please post the best routine to remove Xubuntu *and* *restore Windows boot system*.

---

### Post by yancek on 2015-03-05
From what I have read as I don't use suspend/sleep, doing that with one operating system and booting into another will almost always cause problems.  You are better off fully shutting down one system when booting to another.  Suspending windows and booting Linux will cause problems for you trying to access a windows partition from Linux.  I don't think this is anything to do with graphics cards.  Maybe someone more familiar with suspend/sleep mode on various OSs will come along with more details.

Before you format Xubuntu and its partition, you better verify that you can boot your windows install.  If you are using the Linux Grub bootloader to boot both Xubuntu and windows and you delete/format the Xubuntu partition you will not be able to boot windows.  You will probably need a windows install/recovery CD.

---

### Post by gordon99 on 2015-03-06
I always close right down one OS before I boot another, as a matter of fact I don't believe I was aware it was possible to do anything other. I know I could probably try to ignore the 'sleep mode' problem but each time I log into Xubuntu it opens with a string of system error warnings, all saying the same thing. I am sure they relate to the 'suspend/sleep' fault.
The deletion of the Grub boot loader and its replacement with Windows boot is something that I certainly need help with.

---

### Post by pmi2 on 2015-03-06
If you just want to get a single working Windows boot, I would assume that you can use a Windows 7 "Repair Disc", or something similar.  After that, and once Windows is running the way you want, you can delete the other partition, and start over with a fresh Linux install (or not).

Aside from that, have you tried the "Boot-Repair" tool?  
It might do the job without having to abandon the OS on your second partition.


[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://ubuntuforums.org/showthread.php?p=10871917#post10871917](http://ubuntuforums.org/showthread.php?p=10871917#post10871917)

---

### Post by Mark Phelps on 2015-03-06
You can actually make your own Wint Repair CD using the Backup feature from inside Win7.  Once you have that, reboot from it and run Startup Repair three times -- that's right, three times.  When you then reboot, your PC will boot directly into Win7.

---

