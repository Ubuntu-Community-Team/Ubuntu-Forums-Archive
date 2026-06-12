---
title: "Upgrading to 12.10 with software RAID"
date: 2013-06-18
forum: General Help
---

### Post by Headcase_Fargone on 2013-06-18
First off, I'm a Linux novice and everything that I've set up on my media server to date has been trial by fire.  I've been running [s]10.04[/s] 11.10 for a while now with a software RAID5 array that took many hours of keyboard head-banging on my part.  I ran into every issue imaginable, possibly because of the fact that these drives are 3TB each in size.  The point is I don't know that I could get it set up again and I certainly don't think I could AND preserve the data on them which is essential at this point.

So here I am wanting to upgrade to 12.10 and doing some cursory research I run into threads like [this]("http://ubuntuforums.org/showthread.php?t=1212513") and many others like it where people are having software RAID issues after updating.  So I'm understandably a bit hesitant about proceeding.

Is there anything I should watch out for in particular?  What method would you recommend for upgrading?

Current setup:
/dev/sde1  = 30GB SSD on which Ubuntu is currently running

RAID drives:
/dev/sda1
/dev/sdb1
/dev/sdc1
/dev/sdd1

These are currently mounted as a RAID5 volume under /media using the built in Disk Utility (and some cmd line commands that I don't even remotely recall now)

Edit:  I just noticed that I am, in fact, on 11.10.

---

### Post by Headcase_Fargone on 2013-06-22
Anyone have some information on upgrading with a software RAID?

---

