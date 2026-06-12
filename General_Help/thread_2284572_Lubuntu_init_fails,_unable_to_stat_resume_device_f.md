---
title: "Lubuntu init fails, unable to stat resume device file"
date: 2015-06-30
forum: General Help
---

### Post by bruce35 on 2015-06-30
So I recently installed hibernate on my Lubuntu 15.04 setup, and it seems to have somewhat messed up my install. When I went to power up my machine this morning, the startup screen seemed to go on for way too long, so I hit F1, and got the following 

> 
could not stat the resume device file /dev/disk/by-uuid/<uuid>


where <uuid> was some partition uuid that I didnt recognize (I dont exactly have them memorized after all). I think it might have been the swap partition.

at which point the boot process would simply hang forever. Oddly enough, when I checked Advanced Options in grub, I had another image available that uses systemd, which handled the startup without any problems. Once in lubuntu, I check the swap partition, which has an exclamation mark next to it in gparted.

As best as I can tell, my options are to find some way to fix the default boot process (dont know if it is upstart or something else?) or set my system to boot using systemd by default.

---

