---
title: "trying to get a bigger partition in Ubuntu"
date: 2013-01-09
forum: General Help
---

### Post by fipm on 2013-01-09
Hello everybody!!
 my problem is that I'm trying to get a bigger partition in ubuntu, because now i have just a little space.
first of all i have a sony vaio with windows 7, and then i installed ubuntu 12.10 downloading the cd, and then turning on the pc with the cd inside for install it.
I read about how to do it in Internet, so i did a De-fragmentation in windows, then i turned on the pc with the ubuntu 12.10 cd, for install gparted and use it, but i cant resize the partitions, i don't know why, or what else i have to do, i show a image about what is happening in the program:
(i want to resize the partition \dev\sda3)
[IMG]http://i.subirimagenes.cl/k/pantaaa.png[/IMG]
(sorry i didn't get this image in English, but i guess that for people who know how to use gparted this wont be a problem)
sometimes that calls my attention the Sign of exclamation close to the name of the partition \dev\sda3 .
well, that is.
thanks you!

---

### Post by Impavidus on 2013-01-09
The /dev/sda3 partition shows up as empty, yet it cannot be empty, as win7 is installed on your machine and must use several gigs in that partition. My guess is that the partition is damaged in some way, so that gparted refuses to modify it. Windows can probably repair it. Most likely, it's the result of defragmenting the partition. Windows hasn't completely finished it and intended to finish at the next reboot.

I suggest you reboot into windows, use a windows tool to shrink that partition, reboot a couple of times to let windows run any repairs it deems necessary and then try again to enlarge your /dev/sda4 and /dev/sda5 that's inside using gparted. You'll have to disable swap, that's /dev/sda6, before you can change /dev/sda4.

---

### Post by dpurgert on 2013-01-09
I take it that /dev/sda3 is the Windows partition?   

you might just do better to mount and use it for storage than trying to resize it so you can get more space in /dev/sda5.

If you really want to resize it, make sure that it's not mounted.

---

