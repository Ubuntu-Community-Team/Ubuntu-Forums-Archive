---
title: "newb with questions"
date: 2006-11-21
forum: General Help
---

### Post by jmv on 2006-11-21
Hi.  I saw a video that someone made of some things they can do with their ubunto destop with XGL + Beryl, and i was intrigued.  I'm not computer illiterate, but i'm not super smart with it either, but i'd like to try to get this going.  I've done the CD image and have ubuntu running off of the CD, but when i went to try to actually install it, i got confused about the different options for the hard drive.  I've got an 80gb hard drive with windows and all that setup on it, and it only has about 8gb of space left (i've been planning on getting a cheap large drive, but haven't had a chance yet).  Can ubuntu co-exist with windows, or does it have to make its own separate partition, or how does that work??  I don't really understand which option i should use when it asks me for that.

Also, i may be getting ahead of myself but i was curious about drivers, such as for the graphics card.  Its my understanding that having more than one set of drivers on your harddrive is a bad thing...   does it work out okay though if they're on separate partitions, or if they're for a different OS??

Thanks,
Jason

---

### Post by gareththegeek on 2006-11-21
Ubuntu can coexist with Windows using dual boot but it will need it's own partition.  If the 80gb harddisk is filled with one big windows partition you need to make the windows partition smaller so Ubuntu can fit in.

You probably wanna choose the option
'Resize IDE1 master, partition #1 (hda1) and use freed space'

(It will say something slightly different if it isn't an ide drive)

Then you can use the slider to choose how big you now want your windows partition to be after resizing and click forward.  For example if you slide it to 50% then half the disc (~40gb) will be left for windows and the other half (~40gb) will be used by Ubuntu.  Ubuntu will set it up so when you start your pc it asks whether you wanna start Ubuntu or Windows.

Since your disk is nearly full you'll need to free up some space first or buy a new disk!!

PLEASE BACKUP ANY DATA YOU WOULDN'T WANNA LOSE FIRST - JUST IN CASE IT GOES WRONG!

HTH
G!

---

### Post by rigol on 2006-11-21
And also don't forget to defragment your harddisk (maybe even multiple times) before any attempt to resize!

---

