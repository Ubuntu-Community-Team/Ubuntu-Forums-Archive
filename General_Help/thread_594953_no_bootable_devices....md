---
title: "no bootable devices..."
date: 2007-10-28
forum: General Help
---

### Post by Matty02 on 2007-10-28
I tried to install Gutsy with a dual boot with XP. I had one disk with 2 partitions. After rebooting it said no operating system found...

I put in my windows xp cd to repair it and it didnt fix it. now I can't boot into anything. I tried the xp and recovery console to see if I could make the xp partition active and i couldnt find how to do it. I deleted all the partitions ubuntu made so now I have my xp partition and 20gb of unallocated space...Now when I try to boot up I get "No bootable devices--strike F1 to retry, F2 for setup utility".

PLEASE HELP ME! I'm sure my XP installation is still there I just cant get it to boot up.

---

### Post by Kizlum on 2007-10-28
You need a boot loader. Try to install grub or lilo.

---

### Post by Matty02 on 2007-10-28
to be honest I would prefer to just get the windows boot loader back on. I've tried using fixboot c:, fixmbr and bootcfg /rebuild and it still doesnt work. I'm sure that my partition isnt active, I just need to know how to do that.

---

### Post by rbmorse on 2007-10-28
The gparted LiveCD will do what you need, but in order to use it you have to be able to download the .iso file and burn it to a CD. 

Once you have that you can use it to boot the problem machine, verify the partition layout and set active and bootable flags for the Windows partition as required for the Windwos installer to fix the MBR.  

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

