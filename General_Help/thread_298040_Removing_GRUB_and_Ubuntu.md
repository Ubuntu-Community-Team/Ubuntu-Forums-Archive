---
title: "Removing GRUB and Ubuntu"
date: 2006-11-12
forum: General Help
---

### Post by somersetsimon on 2006-11-12
After my probable hardware issues ([http://www.ubuntuforums.org/showthread.php?t=298038)](http://www.ubuntuforums.org/showthread.php?t=298038)), I'll probably have to remove the hard drive that contains my linux installation. I'm pretty sure that GRUB is installed on the disk that contains my XP. How can I remove GRUB so that, when I unplug the second hard drive, windows will boot up as normal without referring to GRUB?

I'm definitely going to have another go with Ubuntu when I get another disk :)

---

### Post by bigken on 2006-11-12
boot from your windows xp cd go to repair console and type fixmbr enter fix boot enter then type exit reboot and your in to windows

---

### Post by somersetsimon on 2006-11-12
That XP machine only cost me £20 and already had XP installed, so there was no restore cd with it. I can boot up with an ubuntu live cd or reinstall ubuntu from the cd (It generally stays active for at least a few hours!). Is there a plan B?

---

### Post by bulldog on 2006-11-12
You can try the Rescue cd,I never did it myself but I'm told it can restore your windows boot loader.

Just give it a try though.

[http://sysresccd.org/Main_Page](http://sysresccd.org/Main_Page)

---

### Post by Sbarton on 2006-11-12
Have a look at this address [http://www.pclinuxonline.com/wiki/DosMbr](http://www.pclinuxonline.com/wiki/DosMbr) it may offer a solution.
regards

---

### Post by somersetsimon on 2006-11-12
> **Sbarton said:**
> Have a look at this address [http://www.pclinuxonline.com/wiki/DosMbr](http://www.pclinuxonline.com/wiki/DosMbr) it may offer a solution.
regards

That looks promising - I'll try it later. Thanks

---

### Post by somersetsimon on 2006-11-12
> **bulldog said:**
> You can try the Rescue cd,I never did it myself but I'm told it can restore your windows boot loader.

Just give it a try though.

[http://sysresccd.org/Main_Page](http://sysresccd.org/Main_Page)


I used Freedos in the end ([www.freedos.org](www.freedos.org)) and did fdisk /mbr and everything worked fine. I'll be back when I get a new drive ;) 

Thanks for your help.

It's odd - now I'm back to an entirely windows environment after about 5 weeks playing with Ubuntu. It's like the last 5 weeks were just a dream.................

---

### Post by bulldog on 2006-11-12
> **somersetsimon said:**
> I used Freedos in the end ([www.freedos.org](www.freedos.org)) and did fdisk /mbr and everything worked fine. I'll be back when I get a new drive ;) 

Thanks for your help.

It's odd - now I'm back to an entirely windows environment after about 5 weeks playing with Ubuntu. It's like the last 5 weeks were just a dream.................

Just look at my sign................:D

---

