---
title: "migrate ubuntu from one hdd to another"
date: 2007-03-05
forum: General Help
---

### Post by darkrad on 2007-03-05
Hi, i'm running ubuntu on a hdd that since some weeks is very noisy. I'm afraid it will broke soon.
I wish to change the hdd without reinstalling all things.
Is there a program or a tutorial on how to obtain it in easy way?
Thanks in advance.

---

### Post by chewearn on 2007-03-05
You can use GParted LiveCD, copy paste you partitions from old to new harddisk, then reinstall grub on the new harddisk.

---

### Post by laidback on 2007-03-05
darkrad, 
I've done this. Provided you have a second hd, I used my USB hd. You can use Gparted from the installation disc or follow this:-
[http://www.ubuntuforums.org/showthread.php?t=346946](http://www.ubuntuforums.org/showthread.php?t=346946)
Look for my entry which I hope explains the process I used.
Remember that you cannot copy a mounted drive, hence the need for the LiveCd.

---

### Post by darkrad on 2007-03-06
ok i used the gparted program:
source is 12gb hdd
dest is 40 gb hdd
- i formatted dest to ext3, then i left 400mb unallocated, then i created an extended partition on those 400mb and created there the linux-swap partition.
- i copied the ext3 from source to dest partition: all went good
- i copied the linux-swap from source to dest partition: all went good
- shut down
- i switch hdd, and remove gparted livecd
- boot pc and it says no boot disk found..
- if in "manage flags" i set the ext3 partition to boot, then after reboot it says: missing operating system
what am i missing? the grub thing? I'm quite unexperienced with that.. is there a guide to fix it? thanks

---

### Post by darkrad on 2007-03-06
ok i followed this tutorial:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
and now it's working again.
thanks

---

### Post by darkrad on 2007-03-06
I have a problem now :( 
The system with the new hdd is a lot slower (every program i start takes ages, even if i open a terminal). System is not fast but with previous hdd was a lot faster than now. The boot process doesn't take too long, but after i login in X everything i do takes ages.
Anybody experienced the same? Any way to fix?

---

### Post by laidback on 2007-03-06
Only thing that comes to mind is to check your BIOS to make sure that to new hd is recorded correctly (in mine I simply press f3 to get BIOS to rescan for hds) and also check that you haven't by some misfortune set the CPU to a slow value. Mine has 2 settings, 1ghz and 1.53ghz, the second produces a much faster machine.
I guess the hd is fitted correctly and the jumper settings are for master.

---

### Post by darkrad on 2007-03-06
in bios i get the hdd as primary master, and i didn't touch any other values. i'm trying to do the procedure again, creating a partition of 13gb ext3 and not the full 40gb. dunno how it could help, but it's just a try, just to do something... :( :( :(

EDIT: obviously it didn't help.. any suggestion?

---

### Post by chewearn on 2007-03-07
Check in your BIOS, see if you have LBA and DMA6 enabled for the harddisk.

---

### Post by darkrad on 2007-03-07
i used [www.feyrer.de/g4u/](www.feyrer.de/g4u/) finally:
```
copydisk wd0 wd1
```
and now i have a decent speed hdd cloned.
dunno what happened about gparted :(

---

