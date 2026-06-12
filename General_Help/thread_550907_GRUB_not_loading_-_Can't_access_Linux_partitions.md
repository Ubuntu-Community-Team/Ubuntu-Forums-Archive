---
title: "GRUB not loading - Can't access Linux partitions"
date: 2007-09-14
forum: General Help
---

### Post by Ederico on 2007-09-14
My problem in brief is that GRUB doesn't load any longer on one of my pcs and the system boots directly to Windows.

I arrived at this situation after I attempted, and succesfully, installed Ubuntu Ultimate Gamers Edition 1.4 on a system already running Ubuntu Christian Edition 2.0 and Windows XP Professional. There was no problem until such a situation prevailed.

However, after I personally considered that I don't need the Ubuntu Ultimate Gamers Edition 1.4 OS on that system because I have it on my laptop, I used GParted to delete its partition and merge the resultant free space into the Ubuntu Christian Edition 2.0 partition. This is where the problem kicks in. GParted reported that all operations were completed successfully, however on bootup GRUB gives an error 22. That means that I couldn't boot into any OS whatsoever. Therefore, upon finding instructions I used my Windows CD in order to use the Recovery Console option where I used the fixmbr command to fix the problem with GRUB. Unfortunately, now the system boots straight into Windows and thus I cannot access my Linux system.

I basically want to fix such a situation by "returning" GRUB to its former self, thus allowing me to access both Windows and Linux as before.

Hope someone can help.

Best Regards,
Ederico.

---

### Post by mikewhatever on 2007-09-14
You would need to reinstall GRUB using either the Super Grub CD or Ubuntu Desktop CD.
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

If you are interested in the reasons for what happened, read the long and comprehensive grub page [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Ederico on 2007-09-15
Thanks a lot mikewhatever, really helpful. I will try that out as soon as I get some blank CD-Rs as I currently lack both those and some floppies. :)

---

