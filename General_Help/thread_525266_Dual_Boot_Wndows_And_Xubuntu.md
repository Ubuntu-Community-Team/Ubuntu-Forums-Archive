---
title: "Dual Boot Wndows And Xubuntu"
date: 2007-08-14
forum: General Help
---

### Post by stewy.23 on 2007-08-14
What is the easiest way to dual boot windows xp with Xubuntu?. I have looked around but tere is so many different ways to dual boot. I Will start from scratch if i have to.

---

### Post by TeaSwigger on 2007-08-14
What is your system please? The kind of processor, the amount of memory and hard drive space in particular should factor into making the best choices.

Do you know much about hard drive partitions?

In general the easiest way is to have a windows install running fine, download the appropriate Live CD, burn it to a CD, boot to the CD, follow the instructions and take the guided, recommended settings. It will set up the computer so that a menu comes up when you start it for several seconds allowing you to choose windows or linux at the press of a button. For most PCs and most users, using the live CD and "default" settings is a great way to start.

---

### Post by stewy.23 on 2007-08-14
Im using a amd athlon 1.6 ghz processor with a 160 gb Hdd and 256 ram upgrading to 700 soon.

---

### Post by stewy.23 on 2007-08-15
anyone?

---

### Post by ugm6hr on 2007-08-15
Have you got Windows on it already?

---

### Post by stewy.23 on 2007-08-15
yes but  i don't care if i have to delete it and start the install over again.

---

### Post by julian67 on 2007-08-15
Just install Xubuntu. It doesn't matter if from live CD or alternate,  its installer will detect your Windows partition, allow you to resize it as you like/automatically and then set up grub to dual boot. If you're new to all this then the live CD is a more user friendly experience.  Before you begin you should defragment Windows C: and also the Windows paging file. You can use [JkDefrag/]("http://www.kessels.com/JkDefrag/") to defrag, it's Free software and very easy to use (just double click the jkdefrag.exe) and use [PageDefrag]("http://www.microsoft.com/technet/sysinternals/Utilities/PageDefrag.mspx") to defragment the Windows paging file. It's a no cost download from Microsoft. 

Whenever you modify disk partitions you should back up valuable data before you begin. The Ubuntu installer is fine and you shouldn't expect any problem from it but accidents can happen so burn any valuable docs etc to CD or DVD or copy them to an external drive or networked storage...anywhere except the machine you're going to modify.

---

### Post by ugm6hr on 2007-08-15
Agree with julian67.

Although I personally like to use the GParted LiveCD to resize partitions.  If you choose this option - use the GParted LiveCD to shrink the windows partition (to whatever size you want) and leave the rest unpartitioned.

Then just boot the Xubuntu LiveCD.  When booted, click on the install option.  Choose *Guided - Use largest continuous free space*, and it will automatically create a Xubuntu partition (primary) and an extended swap partition for you.  Should then just work when you reboot.

---

### Post by az990tony on 2007-09-02
I have Windows XP and Ubuntu 7.04 dual boot.  I first separated my Windows OS/programs from my data.  Here are the steps:
[http://www.ibm.com/developerworks/blogs/page/InsideSystemStorage?entry=separating_programs_from_data](http://www.ibm.com/developerworks/blogs/page/InsideSystemStorage?entry=separating_programs_from_data)

I shrunk the C: drive to 15GB.  Used Gparted to create a secondary EXT3 partition for Ubuntu.  and had the Swap and D: drive in the Extended partition.

I chose to use the Alt-CD so that I put Grub on the secondary EXT3 partition, leaving my MBR the original Windows version, then updated the boot.ini to use the NT Loader to launch Ubuntu.  This worked well for me.
[http://www.pmg.lcs.mit.edu/~chandra/install/install_dualboot.html](http://www.pmg.lcs.mit.edu/~chandra/install/install_dualboot.html)

---

