---
title: "RAID1 + ubuntu 12.10 = what am I not doing?"
date: 2013-07-16
forum: General Help
---

### Post by catnip_X07 on 2013-07-16
I have two, 2 TB hard drives.  One is /sdd the other is /sde.  

I setup RAID 1 using BIOS and identified the these two, 2TB hard drives, as part of the RAID 1 setup.  However, I cannot find these harddrives under Devices nor is there a RAID icon.  Using GParted I see the drives, and both are currently unallocated. I'm guessing that I have no idea how to get RAID to be setup properly??  I also suppose I was not successful in trying to find my error.  Any assistance would be greatly appreciated.

---

### Post by newbie-user on 2013-07-16
I would suggest configuring a software RAID during the Ubuntu install instead of using BIOS settings, or get a RAID card if you want real hardware RAID. The "RAID" functionality on those consumer motherboards are fakeRAID, and don't really conform to any real standard, so try not to use it. In the BIOS, just disable the RAID.

---

### Post by catnip_X07 on 2013-07-17
If I already have ubuntu installed, just user the install cd to set up RAID?

---

### Post by newbie-user on 2013-07-17
Here's how to do it after an install is already completed: 

[http://ubuntuforums.org/showthread.php?t=1687994](http://ubuntuforums.org/showthread.php?t=1687994)
[http://feeding.cloud.geek.nz/posts/setting-up-raid-on-existing/](http://feeding.cloud.geek.nz/posts/setting-up-raid-on-existing/)
[http://beeznest.wordpress.com/2011/10/18/creating-a-software-raid-array-on-an-already-installed-ubuntu-11-04/](http://beeznest.wordpress.com/2011/10/18/creating-a-software-raid-array-on-an-already-installed-ubuntu-11-04/)

---

