---
title: "Hardware RAID 1 driver"
date: 2008-06-06
forum: General Help
---

### Post by dalym on 2008-06-06
New to RAID and Ubuntu I'm hoping to get clarification and help on these topics as at the moment I love Ubuntu but hate RAID. I need a raid system that keeps running when one drive dies. I have what I've been told is a motherboard that supports hardware RAID 1. MSI K9AGM3 with seperate controller and chipset for RAID (SB600) support. I've done the BIOS thing and was under the impression that Ubuntu's kernel has built-in support for RAID. Therefore once I install ubuntu and partition the drive, should this not be reflected in the mirrored drive, in addition to any applications, modules and data placed on the first drive.

Thank you in advance,

Mark

---

### Post by NT4usB on 2008-06-07
My MB has a Promise RAID chip on it. I struggled for hours, trying to make it go.
Gave up and set up a software RAID.
Uses the same connections, once you've changed them from (whatever) to IDE in the BIOS.
From what I read, every bit as reliable as a hardware RAID.
Some reading:
[http://linux-raid.osdl.org/index.php/Linux_Raid](http://linux-raid.osdl.org/index.php/Linux_Raid)
[http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org++%22software+raid%22&btnG=Google+Search](http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org++%22software+raid%22&btnG=Google+Search)

---

### Post by dalym on 2008-06-13
Yeah, I've had to resort to software RAID now. I followed the instructions here:
 [http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

no joy yet though. I'll have a look at your links and see how it goes but I think I've been beaten to death over the head by RAID.

Thanks

---

