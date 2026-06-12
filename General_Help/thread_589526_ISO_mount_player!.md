---
title: "ISO mount player!"
date: 2007-10-24
forum: General Help
---

### Post by UK-Wobbie on 2007-10-24
I like a tool for Ubuntu what will Mount Game ISO files!
I have had a go using AcetoneISO2 but when i play the ISO with Wine it keep on saying "CD NOT IN DRIVE" I like it so i do not need to put the CDs in the drive i can play the CD Image from my Computer.

Do any one know a tool what can play ISO files? And saves putting in the CD all the time. :lolflag:

---

### Post by ddrichardson on 2007-10-24
I'm not sure how Wine checks this but you can mount an ISO from the command line:```
sudo mount foo.iso /media/bar/ -t iso9660 -o loop
```
Obviously you would need to create the folder "bar".

---

### Post by jkeyes0 on 2007-10-24
did you rerun winecfg and add a cdrom drive for wherever you mounted the ISO?

---

### Post by karth on 2007-10-24
Wine understands simili-symlinks by binding Linux devices and mount points into wine, via winecfg > Drives

I guess you'd just have to mount the image using the previous command, and bind it in wine

---

### Post by UK-Wobbie on 2007-10-24
> **jkeyes0 said:**
> did you rerun winecfg and add a cdrom drive for wherever you mounted the ISO?

Hey thanks for the replays :)

ddrichardson,
I have a go on the command line in a bit and see if that makes it work.. Thanks

jkeyes0,
How do you do that? rerun winecfg and add a cdrom drive?
Am all good in one way and one way am bad at like this. :lolflag:

---

