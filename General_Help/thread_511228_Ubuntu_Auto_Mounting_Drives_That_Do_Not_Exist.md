---
title: "Ubuntu Auto Mounting Drives That Do Not Exist"
date: 2007-07-27
forum: General Help
---

### Post by evolving_monkey on 2007-07-27
I  didn't see a post that seems to cover this specifically when I searched.

In gnome as well as kde an additional cdrom and floppy are mounted that do not exist. Also, I have two additional partitions I use. An ntfs partition and a small 10 gig fat32 partition. The ntfs partition gives me no problems. Even read and write with ntfs-3g seems to work like it's natural.. The 10gig fat32 partition, however,  only shows up in gnome. I can't see the 10gig fat32 partition in kde unless I log into gnome, mount it, log out and then log into kde without rebooting. If i reboot the drive is no longer visible in kde. I even tried checking the auto mount option in kde. It still went away after reboot. (I guess I should mention that I use Ubuntu but I loaded the kde-core so I could play with kde.)

This isn't a huge problem as I usually use gnome but it sounds like something I should try to fix  When I blow these things off I usually realize in a pinch I should have fixed it.  Trying to learn the art of being proactive

Small side question. What is the best way to auto mount the 10gig partition in gnome. In kde you simply check a box (if the drive shows up)  but I haven't seen that in gnome.  

Thanks for your time.

---

### Post by evolving_monkey on 2007-07-27
I took a closer look at the additional drives reported. They are reported like this:

cdrom
cdrom0
cdrom1

floppy
floppy0

the 'cdrom' and 'floppy' icons have a curved arrow on them When I clicked properties it says that their targets are cdrom0 and floppy0 respectively. It looks like these are just shortcuts. The funny thing is that they show up like this even after a reload of the os. (I had to reload in the past because I broke out with some noob wisdom that wasn't so wise.) 

This is what it looks like in case I didn't explain it well. I'm not sure if it's all connected but here you go.

---

### Post by evolving_monkey on 2007-07-29
I've been looking around and I still haven't found a solution. If anyone has any ideas please let me know.

Thanks again for your time.

---

