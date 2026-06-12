---
title: "RAID with one external and one internal"
date: 2007-07-22
forum: General Help
---

### Post by richjoyce on 2007-07-22
Hey everyone,

Due to poor support of my onboard SATA controller, i just moved my internal SATA drive to an external enclosure on my personal server.  My server only has room for one internal drive, and now with that space empty, i'm thinking of putting an IDE drive in there.  But here's my question,

I want to set up a (software) RAID 1 system if it's possible with this setup, it would be:
1 500GB IDE internal drive
1 500GB USB external drive

Also, is it possible to set up the RAID1 on say, 200GB of each drive, leaving two 300GB partitions not RAID'ed for a total of 200GB under RAID 1 and 600GB not RAID?  

I've never done RAID before, so I'm not really sure how the setup works, so any help with my questions would be much appreciated before I go and buy another hard drive!

---

### Post by brent113 on 2007-07-22
Look at this website: [http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188)

Just change the line sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sda1 /dev/sdb1 /dev/sdc1 --auto=md with:
```
sudo mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sda1 /dev/sdb1 --auto=md
```

And of course, replace the names with whatever your harddrives are named.

If you have any other questions, just let me know.

And yes, you don't have to use the entire drive, just make your partitions as big or as small as you want (although they have to be the same size).

---

