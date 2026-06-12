---
title: "FAT32 partition seriously damaged"
date: 2006-12-10
forum: General Help
---

### Post by NiksaVel on 2006-12-10
hey all,

after every 30 mounts, ubuntu automatically checks the integrity of my FAT32 partition - how kind of it :)

Now, the problem is that the last two times it did that, the following happened - the files that were saved to the partition were made either inaccessible or disappeared completely - lost a bunch of albums of mp3s, load of wallpepers I spent a better part of the day collecting and some work documents...

On the other hand, a load of files I deleted during the period of last two weeks were kind enough to reappear and take up storage again, but they were also inaccessible...



WHAT THE HELL IS THAT????   


While it's tempting me to remove the FAT32 partition and just resize ext3 and use that, it will make it more difficult to dual boot...


Also, there is that nice thing that started bugging me about the same time this happened - the fat32 partition becomes read only all by itself for no apparent reason - and I have to remount it to be able to write to again...



somebody please help me....  I almost threw my laptop out the window today...

---

### Post by NiksaVel on 2006-12-11
bump

some1 pls help

---

### Post by smoker on 2006-12-11
sounds like your hard drive may be faulty. download 'drive fitness test' from here:

[http://www.hitachigst.com/hdd/support/download.htm#DFT](http://www.hitachigst.com/hdd/support/download.htm#DFT)

burn it to a boot disc/cd and run it. it will tell you if it is your actual drive that is faulty

---

### Post by technodigifreak on 2006-12-11
> **NiksaVel said:**
> Also, there is that nice thing that started bugging me about the same time this happened - the fat32 partition becomes read only all by itself for no apparent reason - and I have to remount it to be able to write to again...



I agree, find out the manufacturer of your HDD, check their website for a diagnostic tool.  Every manufacturer that I know of has a tool to check for hardware issues.  Also, check out SpinRight @ GRC, it will help correct errors that crop up over time. 

Another funky thing that I noticed is if the FAT formatted drive is a Windows users's My Doc's (or any My % folder), Linux may read them as a readonly partition/folder.  Often they have to be mounted and chown'd for a linux machine to be able to read from them.  Just an odd curiousity I thought may help you find out the issue.  I've only encountered that one one machine, so it may simply have been a gremlin.

---

