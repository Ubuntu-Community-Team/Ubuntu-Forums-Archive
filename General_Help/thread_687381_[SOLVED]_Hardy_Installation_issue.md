---
title: "[SOLVED] Hardy Installation issue"
date: 2008-02-04
forum: General Help
---

### Post by dondad on 2008-02-04
I have 2 har drives on my system.In a previous incarnation, I had 7.04 on one drive and then installed Gutsy at tribe 4 on the other drive, eventually transitioning to that drive as Gutsy was released. Last night I decided to install Hardy on the drive that had 7.04 on it as a dual boot so that I could start playing with it and maybe help find some bugs. The computer is set up as:

sdb has Gutsy with a root partition, one for /home and another for swap.
sda is the drive where I want to install Hardy. It has partitions for root, /home, and swap. The /home still has data on it from the 7.04 install.

I downloaded the Hardy alpha 4 iso, did an md5sum on it and then had it verify the cd when I booted it. I did the install using manual partitioning and had it format the root directory, but not the /home (this is on sda). It appears that it automatically formatted both swap partitions (sda, and sdb) during this install. (why did it format sdb swap when it was not part of the install?)

After the install, I booted Hardy and played with it just a bit to make sure it was runing, then rebooted to get back to Gutsy. That was when the problem started.


It booted to the logon screen, then after logon, dropped to the black screen and command line. It had an error that said something to the effect that uuid xxxxx not recognized in fstab and that the /home did not exist. I messed with it a bit, but did not have the time to try to debug as I needed the computer this morning, so I reloaded Gutsy and life was good.

This same thing happened with the alpha 3 release, but that time, Hardy would not boot at all, so I figured that I had a bad cd, hence the testing before I loaded alpha 4. I didn't have time to see if Hardy would still boot, but will try tonight. Any ideas what might be going on, or how I can provide data to help debug?

---

### Post by plucky on 2008-02-04
dondad,

I think the problems you are having is caused by the **UUID** changing when you do a new install.
What happens is the **Fstab** is expecting a UUID that it found when the OS was installed is not the same, as the new install has changed it to something different and it is unable to resolve it.
You should find that when you boot Hardy you should get the same error as you got when booting Gutsy,before you reinstalled it. You should be able to continue to boot by typing **CTRL D** and it will continue to login screen.
After you login, open a terminal screen and type ```
blkid
``` and ```
cat /etc/fstab
``` and compare the UUID's of each partition, I think you will find the ones for your Gutsy partitions have changed.If they are different, you have to edit your **fstab** file to reflect the new UUID's.


Good luck

---

### Post by dondad on 2008-02-04
Thanks, I will take a look at that tonight. I guess that I am curious as to why it never did this when I did the same thing going from edgy to gutsy.

---

### Post by dondad on 2008-02-04
> **plucky said:**
> dondad,

I think the problems you are having is caused by the **UUID** changing when you do a new install.
What happens is the **Fstab** is expecting a UUID that it found when the OS was installed is not the same, as the new install has changed it to something different and it is unable to resolve it.
You should find that when you boot Hardy you should get the same error as you got when booting Gutsy,before you reinstalled it. You should be able to continue to boot by typing **CTRL D** and it will continue to login screen.
After you login, open a terminal screen and type ```
blkid
``` and ```
cat /etc/fstab
``` and compare the UUID's of each partition, I think you will find the ones for your Gutsy partitions have changed.If they are different, you have to edit your **fstab** file to reflect the new UUID's.


Good luck
Thanks, that was it. It didn't boot into Hardy, but I edited the fstab to match the gutsy one and it worked fine. Funny thing is that I don't remember this happening when I did the same thing from Edgy to Gutsy, but then I also have problems remembering what I had for breakfast. ;-)

---

