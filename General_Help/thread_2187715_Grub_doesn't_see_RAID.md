---
title: "Grub doesn't see RAID"
date: 2013-11-13
forum: General Help
---

### Post by feffer on 2013-11-13
This machine has Win7 on an OCZ PCI Express card configured as a RAID. On a separate hdd it has Ubuntu and some other linux distros. These are NOT part of the RAID or on it. Currently, the machine default boots into Win7. To get to linux, we must boot from the BIOS. Then the GRUB menu comes up. It shows all the linux distros, but not Win7. In any case, one can boot everything, but this is a clunky way of doing it. I want GRUB to come up immediately instead of invoking the BIOS boot menu, but I can't because GRUB doesn't see the RAID (with Win7 on it). 

I tried opening gparted and it has some issues about mixing GPT and msdos partition tables. If I lie and say there is no GPT, gparted will open but it shows four separate 60GB drives rather than a single 240GB RAID on the OCZ card. I tried loading a linux driver from OCZ's website. The module seemed to load successfully, but I don't know how to check for sure. I'm not sure I even need this driver since it's not on the RAID. In any case, gparted is still not seeing the RAID. It seems like there are a couple of issues going on here, but I've hit the wall. How can I resolve this? thx!

---

