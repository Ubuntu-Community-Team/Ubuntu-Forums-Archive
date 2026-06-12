---
title: "moved partition messed up my system"
date: 2007-08-13
forum: General Help
---

### Post by snkiz on 2007-08-13
I should have read up first. Hindsight is 20/20, So I decided to move/resize the partitions in my computer( the way I thought I would use them turned out way diffent than reality)first I had to throw my live cd in because gparted wouldn't do anything but look when I ran it from in ubuntu. then I reformated my swap(hda1) because gparted said it was damaged (resized it to) then I copied  my /boot partition so I could move it I actualy made two copies so I could "shell game" one the copies into the old /boot tile of hda2. so far so good. then I unformated a fat32(hda3) and fat16(hda4) so I could make them into one ext3(hda3). peachy so far. My root file system(hdc2) and /home(hdc1) are on another disk I didn't touch them. After that was all done my mount points were very messed up, but I managed to figure out the nessary changes in fstab (UUID's had to be changed) Now the problem I'm at a loss to explain is the seemingly random files that no longer open when I click on them, However if I use the appropiate program to open them its fine eg: screenshot.png gives me an error that reads 
Cannot open /home/ck/Desktop/Screenshot.png: No application suitable for automatic installation is available for handling this kind of file.
but if i use an image viewer its all good. This is not limited to .png files .desktop .jpg .tar I'm sure there are more. also when I click on the computer icon all the launchers for my disks are broken even though the links on my desktop and in the places menu are fine. I'm lost no idea where to even look to fix this one.

---

### Post by snkiz on 2007-08-13
17 hours??!!? ok so whats the magic password to get some help here??

---

