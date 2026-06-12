---
title: "grub error 18"
date: 2008-04-13
forum: General Help
---

### Post by charbilas on 2008-04-13
Hello
I installed ubuntu 7.04 on a computer that has a harddrive 160 GB.Bios doesn't see it as 160 GB but as 136GB. I think that for this bios is the limit. In this harddrive I allready had install winxp on a partition of 136 GB so I made an ext3 partition and a swap partition to the other 13.2 GB as it said.
Linux copied the files but when the computer rebooted grub wouldn't start. I tried super grub but when I asked to go to the boot of linux it said error 18.
Then I searched in the forum and I found out that its a problem of bios and that I should move the boot record in the beginning of the harddrive. Is this possible without losing the data that I allready have on the windows partition?
Thanks 
Christos

---

### Post by louieb on 2008-04-13
You can use GParted available on the [SystemRescueCd]("http://www.sysresccd.org/Main_Page") or [PartedMagic]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic") or some other partitioner to shrink your window partition.  Most of the time this is done without harming windows. But still its best to backup those things you can't afford to loose. 

  Then you can [ make a separate /boot partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition") and put it in the 1st 137 or so GB of the partition.  

GRUB error 18 is the only reason I would have a separate /boot. Its not that hard but is a little daunting for those new to partitioning and Linux.

Post any questions you might have.

BTW: Have you checked your computer makers website for a BIOS upgrade?

---

### Post by charbilas on 2008-04-14
Thanks for helping
well I finally put another hardrive primary slave and reinstalled ubuntu but I didn't erase the previous installation on the other hardrive. I'm trying to find bios update for the motherboard I have, but its very old
maybe I should buy another newer.
I'll try what you said and let you know

---

