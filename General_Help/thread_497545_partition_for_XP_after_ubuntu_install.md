---
title: "partition for XP after ubuntu install"
date: 2007-07-10
forum: General Help
---

### Post by bhuthogg on 2007-07-10
Hi.

I have installed Ubuntu and fully intend to keep it as my primary OS but im looking to make a small 50/60gb partition so i can Have XP and the option to boot into one or the other  as i have a couple of programs i like to record and play around with.
I've tryed emulating XP and had bad results for memory intensive programs, 

So basically im just looking to do the opposite to what all the guides ive found for dual booting the 2. 

thanks for reading :D

---

### Post by dabl on 2007-07-10
> **bhuthogg said:**
> 
I've tryed emulating XP and had bad results for memory intensive programs, 


Did you try VMWare Player 2.0?  It's free and works great for me.

My experience installing dual boot about a dozen times (trying to get it right) was that you really, really, really want to put Win XP on first, and Ubuntu on second.  Otherwise, you'll need a consultation from a guru and a whole bunch of fancy Grub editing and file-moving to get a working boot menu. :)

---

### Post by Happy_Man on 2007-07-10
No, sorry, you can't install XP after Linux because then XP will cry shout scream and refuse to boot. Furthermore, it will erase GRUB, so that Ubuntu becomes incapable of booting also. There is only one thing to do now - back up all your data, wipe the HDD, install Windows, and then reinstall Ubuntu. Sorry.....

---

### Post by marsbt on 2007-07-10
The thing to keep Windows happy is that you should install it on the first partition on your HDD. Although not a strict rule (as I have run it on other partitions and even second hard disk) it is helpful in order to have lesser problems. So if you want to follow the easy way, you can do as **Happy_Man** and **dabl** suggest. And if you are really new to Linux, go the easy way ;)

However, Linux being linux and not Windows, can be tweaked and GRUB can be reinstalled even if it is lost after a Windows install (barring the case when you install Windows over your Linux after formatting partitions). It isn't that hard to reinstall GRUB either. All you need is the will to follow instructions and learn.

---

