---
title: "Issues after Kernel Compile (2.6.20)"
date: 2007-02-13
forum: General Help
---

### Post by LycoLoco on 2007-02-13
I was running out of space on my partition for Ubuntu tonight, so after doing some reading, I copied my existing partition (hdb2) over to another partition I had (hda6). Everything worked perfectly and I now have an additional 5 gigs to play around with. The main reason I did this is because I didn't have enough room to compile a new kernel, so after I rebooted, that's what I did. 

The compile went perfectly, but when I rebooted, I noticed that it wrote the /boot/grub/menu.lst as if it were going to boot from the old partition (hdb2). Luckily I hadn't deleted that partition yet, so I booted into the old installation, edited menu.lst to reflect the changes, and rebooted. This time I tried to boot into 2.6.20, but it said Grub Error 15: File Not Found. I sighed, and booted into 2.6.17-11 and looked in /boot/grub to see if the files were indeed missing, but they weren't. Does anyone know what this might mean and how I can fix it, as well as what I need to change to make the next compile use hda6 in Grub instead of hdb2? Thanks!

---

