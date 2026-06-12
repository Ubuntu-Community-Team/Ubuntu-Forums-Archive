---
title: "Invalid arch independent ELF magic error on Ubuntu 12.04.2 LTS with a GPT"
date: 2013-07-07
forum: General Help
---

### Post by Maru90 on 2013-07-07
Hi, 

I was following the guide on this [help.ubuntu]("https://help.ubuntu.com/community/MakeALiveCD/DVD/BootableFlashFromHarddiskInstall") page to create a live CD from my system, which went fine, but after restarting my laptop the error occurred. I'm note sure why, but I suspect something happend after I ran the ```
 sudo apt-get install grub2 ... 
``` command, as it tried to install the grub2 bootloader on my own system. Anyway, after searching these forums for a while I found these helpful posts at [http://ubuntuforums.org/showthread.php?t=1870369](http://ubuntuforums.org/showthread.php?t=1870369), starting at reply #5. Unfortunately, I'm not that familiar with UEFI booting, so any help at all as to how I would recover the boot-loader would be much appreciated. 

I also tried running the boot-repair tool, which reports an error when finished and was unable to resolve the error. It produces [this]("http://paste.ubuntu.com/5853900/") boot info summary.

---

### Post by Maru90 on 2013-07-09
Managed to solve this on my own, all that was needed was to reinstall grub2 on the efi partition. As shown [here]("http://superuser.com/questions/376470/how-to-reinstall-grub2-efi").

---

