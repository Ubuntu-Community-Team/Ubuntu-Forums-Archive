---
title: "Issue with accessing system files on chromebook running ubuntu"
date: 2020-04-28
forum: General Help
---

### Post by jojoivy on 2020-04-28
I am very new to Ubuntu, and I just got it running in developer mode on my chromebook alongside chromeos. I was attempting to install a program when I realized that my system listed way less available storage then there should be (my chromebook should have a max of about 32gb, and it was telling me I had about 11gb max). I checked the file system and realized that not only is it refusing to mount the drives (or partitions, I'm not sure) that are labeled ROOT-A, OEM, etc., it also refuses to mount an SD card I plugged into it (formatted to fat32). Chromeos is having no issues with the SD card.

---

### Post by TheFu on 2020-04-28
ChromeOS has 2 copies of the OS so that 1 can be updated by google whenever they like.  The other copy, which is running, is mounted read-only as part of the security methods used by google on ChromeOS.  Local storage for each user under chromeOS is encrypted, so other OSes shouldn't have access.

As for access to the SD card data, there are different file systems.  Depending on the version of ubuntu run,  some support for proprietary file systems
is not automatically installed.  You can install the support, most likely.  Just post the file system type and we can probably help assuming the SD controller driver is compatible with the SD card.

Update: ooops, see that you think the card is FAT32.  Most desktop linux distros should support that, but most new SD cards over 32GB in size would be exFAT.

---

