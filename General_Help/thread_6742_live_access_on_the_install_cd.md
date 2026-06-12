---
title: "live access on the install cd?"
date: 2004-12-01
forum: General Help
---

### Post by snipes420 on 2004-12-01
Is there anyway i can use the install cd to access the already installed system on my drive? 
I installed ubuntu then installed windowsafter in a seperate partition. I had read in another thread that i can use the live cd to fix the grub bootloader but at the time I thought that the install cd had these live capabilities. unfortunately when i tried to boot from the cd and started pressing f1 f2 etc I didnt see anything about live anything.  

Is there anyway I can fix the bootloader without having to download the live CD?

I was thinking it would be a great option to have on the install cd. a option that can repair grub without needing a seperate cd. 

Thank you for your time.

Edit: ok, i ended up downloading the live cd anyway. But I think it is still a great idea to have a option on the install cd to reinstall the bootloader. if that is possible. perhaps entering something like this at the boot: prompt: "linux fixgrub". or "grubfix"

---

### Post by asplode on 2006-07-18
There sure is.

[vnbuddy2002's guide to restoring GRUB]("http://doc.gwos.org/index.php/Restore_Grub")

---

### Post by cjm5229 on 2006-07-18
> **asplode said:**
> There sure is.

[vnbuddy2002's guide to restoring GRUB]("http://doc.gwos.org/index.php/Restore_Grub")

That doesn't work with the Dapper Drake Alternate CD, it won't install 
grub without installing the base system first. Usually screws your Root Partition in the process. You should be able to do it through the repair option though. I have not succeeded in doing that way yet, but it is suppesed to work.

---

