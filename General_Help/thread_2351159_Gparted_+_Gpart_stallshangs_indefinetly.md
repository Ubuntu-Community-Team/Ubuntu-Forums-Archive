---
title: "Gparted + Gpart stalls/hangs indefinetly"
date: 2017-01-31
forum: General Help
---

### Post by javierdl on 2017-01-31
... as soon as I choose for it to run data recovery.
I need to analyze a disk for data recovery, but when I try it freezes.

Any pointers?

Thanks

JDL

---

### Post by DuckHook on 2017-01-31
Need far, far more info. Cannot possibly help with no data. :(

Disk info? Type of partition? Filetype? What happened? Why recovery? What do you need to recover?

Although knowing nothing about your situation, *gparted* is not a robust data recovery tool. Instead, try the following:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[https://ubuntuforums.org/showthread.php?t=1958605&p=11846293#post11846293](https://ubuntuforums.org/showthread.php?t=1958605&p=11846293#post11846293)

---

### Post by javierdl on 2017-02-01
> **DuckHook said:**
> Need far, far more info. Cannot possibly help with no data. :(
Right you are!

> Disk info? 
Disk with lost partition: WDC WD10EZEX-21M2NA0, 1Tb, GUID Partition Table, EFI system

> Type of partition? 
 GUID Partition Table

> Filetype? 
Ext4

> What happened? 
Windows 10 decided to format the neighbour partition when I installed it ...

> Why recovery? 
...(which I had not backed up) :(

> What do you need to recover?
blender files, photos, and videos
-----------------------------------------------------------------------------------------

I have been trying TestDisk now.
I have Analysed, and Deep Searched, but I am getting this message: "***Can't open filesystem. Filesystem seems damaged.***"
I don't see options in TD to repair the filesystem, is there one?
Btw, I am running TD from a SSD with Ubuntu. The HD has Win10.


Thanks

---

### Post by DuckHook on 2017-02-01
> **javierdl said:**
> …(which I had not backed up) :(:sigh:

…the amount of heartache and grief that people would spare themselves if only they backed up…

> I have been trying TestDisk now.
I have Analysed, and Deep Searched, but I am getting this message: "***Can't open filesystem. Filesystem seems damaged.***"
I don't see options in TD to repair the filesystem, is there one?
Btw, I am running TD from a SSD with Ubuntu. The HD has Win10.Thanks
The most important thing on those links is the advice that you must work from a clone. DO NOT USE YOUR HDD any further. Continued writes to it only diminish your chances of data recovery. You must clone that HDD to another, even an external USB HDD will do, but no further use.

As it happens, another poor soul is going through exactly what you are, but in reverse. He is trying to recover Windows data that he overwrote with an Ubuntu install: [https://ubuntuforums.org/showthread.php?t=2351165](https://ubuntuforums.org/showthread.php?t=2351165)

You may find TheFu's advice in that thread useful.

Before more instructions, *make that clone*. Instructions are in my first link.

---

### Post by javierdl on 2017-02-02
I've got Clonezilla Live USB, I shall do that that file to clone the disk in an USB drive asap. And attempt the recovery from it.
Thank you so much for the advise DH :)

---

### Post by DuckHook on 2017-02-02
Use gddrescue as per the following subsection of the above referenced thread: [https://help.ubuntu.com/community/DataRecovery#Imaging_a_damaged_device.2C_filesystem_or_drive](https://help.ubuntu.com/community/DataRecovery#Imaging_a_damaged_device.2C_filesystem_or_drive)

You need a utility that does a literally bit for bit copy.
```
sudo apt install gddrescue
```

---

### Post by javierdl on 2017-02-03
DH, 
Thanks for insisting for me to work off of a cloned drive as opposed to the original. I am now.
Btw, I tried using Clonezilla Live, but it didn't load in EFI, I guess it can only do it in classic BIOS mode. Plus I do recall not having a very pleasant experience with it in the past, a rather confusing interface. I ended up doing the cloning with AOMEI Backupper, way easier in every way.

Thanks for sharing about using gddrecue too. Should I understand that when one encounters that error message [COLOR=#000000]*"*[/COLOR]***Can't open filesystem. Filesystem seems damaged.*" **that's as far as one can go with TD? Reason why I should switch to gddrescue?

Thanks again,

---

### Post by DuckHook on 2017-02-03
The word "clone" is a vague one. Many utilities that call themselves "cloning" software actually only make copies of readable files, which is pointless since the files you are trying to recover are the unreadable ones. They don't actually do bit-for-bit cloning, which is what is needed in this case. I don't use Windows and have no idea how AOMEI Backupper works, but I do know that gddrescue makes a bit-for-bit copy. Your target disk will be an *exact* replica of your source disk. This is why you would then be able to work on it properly. Don't let the "rescue" part of the name mislead you. It is mainly a very powerful, true cloning utility.

Concentrate on the [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) wiki article. The actual recovery software is about midway down into the wiki article: Foremost, Scalpel, Magic Rescue, Photorec and recoverjpeg. Many people in similar trouble report good results with photorec.

All such utilities are rather involved. There's no "easy" way to do what you're trying to do. You will need to Google for guidance. YouTube might also have tutorials that can help. If you run into a dead end, then use gddrescue to make another clone and start over. That's the beauty of the cloning strategy.

Some tutorials found through a simple Google search follow:

[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.ghacks.net/2015/04/20/how-to-use-photorec-gui-to-recover-lost-digital-photos-and-files/](http://www.ghacks.net/2015/04/20/how-to-use-photorec-gui-to-recover-lost-digital-photos-and-files/)
[https://www.youtube.com/watch?v=EJdx2ORi3r4](https://www.youtube.com/watch?v=EJdx2ORi3r4)

Please be mindful that I have not vetted these tutorials and have no idea if they explain things effectively or are even accurate. I'm just giving you some leads to go on. It would be best comparing a number of different tutorials to make sure they are consistent.

Let us know how it goes.

---

### Post by javierdl on 2017-02-14
Btw, I did try Gparted + Gpart again, I was able to notice that it was not frozen, it was doing its thing, except it was not obvious. So I let it finish. It took well over an hour, but it did it. Unfortunately it was not able to recover anything. But at least that mystery was solved.
So far I was able to find my files thanks to EASEUS Data Recovery Wizard.

---

