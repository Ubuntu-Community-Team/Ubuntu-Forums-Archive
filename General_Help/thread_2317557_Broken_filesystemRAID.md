---
title: "Broken filesystem/RAID"
date: 2016-03-17
forum: General Help
---

### Post by john-travis-green on 2016-03-17
Well. Darn. So, I had a RAID0 setup across two drives. Was scrolling through my bash history and accidently hit enter on one of the two for tune2fs /dev/sd??? (??? = not sure which). Rebooted. Then I was dropped to the intramfs prompt. I booted from a backup usb drive and ran sudo dumpe2fs /dev/sda1 |grep superblock (one of the RAID members) and Im getting Corrupt extent header while reading journal super block. 

What Im nervous about is breaking my raid. Some articles addressing this obstacle seem straightforward for single drive systems, but what about a raided system? 

Thanks for the help in advance,
John

---

