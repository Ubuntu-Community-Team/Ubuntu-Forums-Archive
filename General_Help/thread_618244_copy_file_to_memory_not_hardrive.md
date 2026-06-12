---
title: "copy file to memory not hardrive?"
date: 2007-11-20
forum: General Help
---

### Post by Sir P on 2007-11-20
Hello all :)

Have a quick question regarding disk/memory space on linux.

If I do a df command I get the following:

> 
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             1.8G  1.2G  493M  71% /
tmpfs                 443M     0  443M   0% /lib/init/rw
udev                   10M   36K   10M   1% /dev
tmpfs                 443M     0  443M   0% /dev/shm


Now, from what I understand those are all listing pyhiscal storage space locations - thats all well and good, I can store a file in each of thjose places if needs be. Great. But now I need to store a file in memory, not in pyhsical storage - where is the pyhsical memory and how would I save a file to it?

Currently I have a file get created/updated/replaced every second or so, its then gets 'mv' 'ed to /root/file - though it reduces the life of my storage media (read write cycle) so im trying to store it in memory..

Is this possible or have I misunderstood?
Any assistance be much apperciated.

Many thanks
Sir P :D

---

### Post by eggdeng on 2007-11-20
Redundant post.

---

### Post by shad0w_walker on 2007-11-20
If memory serves (Pun not intended) then you can put things into RAM using the /dev/shm folder. Just remember to copy it out of RAM when you're done. Don't want to forget about it and have it nuked when you reboot or anything.

---

### Post by eldragon on 2007-11-20
this should point you to the right direction:

[http://www.vanemery.com/Linux/Ramdisk/ramdisk.html](http://www.vanemery.com/Linux/Ramdisk/ramdisk.html)

---

