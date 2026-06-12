---
title: "How to reproduce Disk Extender feature of Windows Home Server on an ubuntu system"
date: 2007-09-27
forum: General Help
---

### Post by vice-amiral on 2007-09-27
Everything is in the subject.

I'm stuck neither with the raid manager or LVM or rsync I'm abale to do it.

Somebody already succed or tried ?

Thanks a lot

---

### Post by dcstar on 2007-09-28
> **vice-amiral said:**
> Everything is in the subject.

I'm stuck neither with the raid manager or LVM or rsync I'm abale to do it.

Somebody already succed or tried ?

Thanks a lot

Linux has many disk features, if you don't just assume that people here know what Windows "Disk Extender" does and actually explain what you are trying to achieve, then you might just get some useful assistance.

---

### Post by vice-amiral on 2007-09-28
Hello, well i was assuming that it was known.

Well Disk Extender is a "new technology" introduced by Microsoft on his Windows Home Server operating system.
To make a long story short this technology allow an user to merge several disk into one single disk space (like a raid JBOD or a like a LV with several PV with LVM) but it offer also the possibility for some directory (selected by the user) to be dupplicated to prevent data loss in case of disk failure (like mirroring in RAID 1).

They can do this with 2 or more disk, the space allocated for mirrored data and "normal data"  change dynamicaly, following the need of the user.

With LVM I'm able to make one big Logical volume there is no problem.

I could also make redondancy on another LV with RAID 1 but:

When I want a folder to be mirrored I have to copy the full folder from one volume to the other. It could take a while, on WHS is done in a second.

Then the space allocated to redondancy must be allocated dynamicaly and this become very difficult to do.

Finally when you have 3 or 4 disks it become a real mess to handle.

I did not find a way to do it smoothly and this is the question. How to do it ?

Another way to do it could have been to use one sigle LV regrouping all PV and then to use rsync to dupplicate the folder for which I want redondancy but how can I do to be sure that the original and the copy are not on the same disk ?

LVM as no RAID 1 feature as far as I know...

Thanks for your help

---

### Post by dcstar on 2007-09-28
> **vice-amiral said:**
> Hello, well i was assuming that it was known.

Well Disk Extender is a "new technology" introduced by Microsoft on his Windows Home Server operating system.
To make a long story short this technology allow an user to merge several disk into one single disk space (like a raid JBOD or a like a LV with several PV with LVM) but it offer also the possibility for some directory (selected by the user) to be dupplicated to prevent data loss in case of disk failure (like mirroring in RAID 1).
.........
LVM as no RAID 1 feature as far as I know...

Thanks for your help

These will help with some of the requirements:

[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)
[http://www.howtoforge.com/linux_software_raid](http://www.howtoforge.com/linux_software_raid)

---

### Post by vice-amiral on 2007-09-28
Thanks,

I check both site but it only about common use of raid or LVM nothing that could help me.

If somebody else have an idea.

Guys ! don't tell me that Microsoft does something we cannot do with Linux :(

---

### Post by Joffer on 2008-01-15
> **vice-amiral said:**
> When I want a folder to be mirrored I have to copy the full folder from one volume to the other. It could take a while, on WHS is done in a second.
Not true. It just "feels" that way. After you choose to duplicate a shared folder, windows will start making a copy on another disk. This takes time. But you might mean that your end of the configuration is done "in a second" and thats true. It's more user friendly.

A good Technical Brief for Windows Home Server Drive Extender can be found here (pdf):
[http://download.microsoft.com/download/2/F/C/2FC09C20-587F-4F16-AA33-C6C4C75FB3DD/Windows_Home_Server_Drive_Extender.pdf](http://download.microsoft.com/download/2/F/C/2FC09C20-587F-4F16-AA33-C6C4C75FB3DD/Windows_Home_Server_Drive_Extender.pdf)

---

### Post by Feclar on 2008-01-19
Yea I am looking for the same solution

No luck yet

Very simple idea and I am sure lots of people would benefit from it

Basically JBOD with redundancy, true not as fast as RAID but... disks are fast enough these days.

---

### Post by Joffer on 2008-01-21
> **Feclar said:**
> Yea I am looking for the same solution

No luck yet

Very simple idea and I am sure lots of people would benefit from it

Basically JBOD with redundancy, true not as fast as RAID but... disks are fast enough these days.

Well, a single disk is most likely faster than RAID-5 for writing.

---

