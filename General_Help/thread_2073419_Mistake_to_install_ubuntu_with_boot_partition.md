---
title: "Mistake to install ubuntu with /boot partition"
date: 2012-10-19
forum: General Help
---

### Post by smartygeek on 2012-10-19
hi
in have windows 7 and ubuntu. I usually use ubuntu for 6 month.
when I wanted to install ubuntu! i mistake !
install ubuntu on 2 partion
/ ( root
/Boot ( 100Mb )
Now evey time i want to update my ubuntu ( kernel ) i got error that "don't have space on /boot "
so how i can chane my /boot partition to root without reinstall ubuntu?
special thanks

---

### Post by MrsUser on 2012-10-20
Perhaps you have old kernels which you can remove. What is the output if you type the following in Terminal?

```
dpkg --list | grep linux-image
```To open terminal, press CTRL+ALT+T

---

### Post by oldfred on 2012-10-20
Housecleaning is a good idea. I think I have 4 kernels in my /boot and it is about 100MB.

Years ago I did move /boot, but then I really wanted a grub only boot partition not a /boot and moved it back.
You have to copy all files from /boot partition back to your /boot folder in / (root) with copy parameters that preserve the root ownership & permissions. You then have to edit fstab to remove the separate /boot entry and reinstall grub to the MBR so it knows to look for grub & kernels in / not separate /boot. Then reboot & hope everything is ok. Best to have current version liveCD and know how to download Boot-Repair just in case.

It is similar to a move of /home.
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Others that really are the same with different copy commands:
Uses cp -ax
[http://www.ibm.com/developerworks/linux/library/l-partplan/index.html](http://www.ibm.com/developerworks/linux/library/l-partplan/index.html)

If you want more details I can post some more info but you may still have to modify commands for your configuration.

---

### Post by smartygeek on 2012-10-20
thanks for answering me ...
this is my result
```
majnoon@smartygeek:~$ dpkg --list | grep linux-image
rc  linux-image-3.2.0-23-generic           3.2.0-23.36                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-26-generic           3.2.0-26.41                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-27-generic           3.2.0-27.43                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-30-generic           3.2.0-30.48                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-31-generic           3.2.0-31.50                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-generic                    3.2.0.31.34                             Generic Linux kernel image

```so now, what can i do?

i also use ubuntu 12.04 ...

---

### Post by MrsUser on 2012-10-20
Ok, you need to remove old kernels. In the course of updating your system over time, the kernel of your Ubuntu system was updated several times. For backup reasons, the old kernels are kept, in case something doesn't work after the update, so that users can go back to the previous kernel.

Anyway, you can clean up the old kernels. You only need the current one. The old kernels are the reason why you ran out of space on your separate /boot partition.

The easiest method is to install Ubuntu Tweak (if you want a solution where you don't need to use command lines in the Terminal). To install Ubuntu Tweak, type the following in Terminal, one by one.

```
sudo add-apt-repository ppa:tualatrix/ppa
``````
sudo apt-get update
``````
sudo apt-get install ubuntu-tweak
```After installation, you will find Ubuntu Tweak in System Settings (or in Dash look for 'Ubuntu Tweak'):
[[IMG]http://i.imgur.com/HOmyNs.png[/IMG]]("http://imgur.com/HOmyN")


Start Ubuntu Tweak, go to the 'Janitor' section.
On the left side, look for 'System' > 'Old kernel'. Make a check. Addtionally, also for 'Apt Cache', if you want to clean up that too. Then press 'Clean' at the very right bottom. It should clean up everything. If something is still left after that, repeat the cleaning until no cruft is left.

[[IMG]http://i.imgur.com/eydoDl.png[/IMG]]("http://imgur.com/eydoD")


(On my screenshot it says '0' for Old Kernel -- this is because I cleaned up everything already).


After the cleaning, you should have enough space again on /boot.

---

