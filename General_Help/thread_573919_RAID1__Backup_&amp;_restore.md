---
title: "RAID1 / Backup &amp; restore"
date: 2007-10-12
forum: General Help
---

### Post by AlliumPorrum on 2007-10-12
I'm just installing a new Ubuntu server for me, which is going to be basically a network multimedia server for other computers and also serves as a MySQL DB server for few apps of mine.

All data in that server is quite important, so first I thought that along with backups I would use RAID1 for securing the data. But HW raid controllers seem to be quite expensive, too expensive for me anyway.  I also read tens of threads about SW RAID in Ubuntu, and it seems to be really difficult to install (for newbie like at least) so maybe I'm not going to go for that either. I don't know if 7.10 is going to make this any easier though..?

So I think that it would be enough if I just backup Ubuntu server's whole HD to my NAS, and in the case of HD failure I buy a new one and restore the whole Ubuntu from that backup. I really would like to backup the whole HD including OS, all applications, MySQL databases and all other data, if it is possible. 

Now, my question is; what would be the best way to do this so that restoration can be done as easily as possible? And if the HD really brokes, how could I restore the whole system from such a backup to a new empty HD that also should be bootable? I think that it's impossible to anyhow backup bootsectors also, but please correct me if I'm wrong.

---

### Post by thirddeep on 2007-10-12
You can create a true copy of the HDD with ghost for unix (g4u).

On a side note, all the good mobo's have RAID on them these days.

Or stick to rsync :-)

Thd.

---

### Post by AlliumPorrum on 2007-10-12
> **thirddeep said:**
> You can create a true copy of the HDD with ghost for unix (g4u).


If the HD fails, how this kind of ghost is then restored to the new HD? Will it also handle boot sectors?

Maybe it would be a good idea to also divide the HD to 2 partitions; other for OS & apps, other for data. Then it would be possible to make an restorable image of the system itself, and ordinary backup of the data files so that they can be restored file by file if needed. Right?

---

### Post by thirddeep on 2007-10-12
G4U uses DD, so it's a true copy of the HDD.

If you HDD fails, put a new one in and dump the G4U image on it ... 

Dividing one HDD up for OS and APPS is -IMHO- utterly pointless.  Either you have the $$ for a RAID1 card, or at least a good mobo with RAID1 on it, or spend 10min reading google howto software mirror.

Fail that, rsync and reinstall after HDD failure.

Thd.

---

### Post by AlliumPorrum on 2007-10-12
> **thirddeep said:**
> G4U uses DD, so it's a true copy of the HDD.

So is it even possible to make an image of just one partition of the HD? Or is it always taken from the whole fysical disk?

> **thirddeep said:**
> 
Dividing one HDD up for OS and APPS is -IMHO- utterly pointless.  


Well I was just thinking that in some cases there is a need to restore just one datafile, so backup for datafiles might be better idea than disk image. And on the other hand; if data files are backup'd, it's pointless to include them to the disk image. Or did you mean something else??

> **thirddeep said:**
> Either you have the $$ for a RAID1 card, or at least a good mobo with RAID1 on it, or spend 10min reading google howto software mirror.

Well I don't have the $$, not even &#8364;&#8364;&#8364;'s... I already did spend few hours for reading stuff about software RAID in Ubuntu, and found out many many articels with tens of pages, and often they had a bit different kind of instructions for doing it. As I said, I don't have much experience with Linux, so if I can't find some **exact** step-by-step instruction for how to do this SW RAID1 and how to re-build after failure, I think it's quite a tough task for me. :confused:

---

### Post by AlliumPorrum on 2007-10-15
Ok, after reading few more hours about SW RAID1, I think that backing up is much more easier way to handle this data securing issue. Few questions still:

If I use just rsync for backing my data, should I really backup all directories starting from the root directory to be sure that the whole system can be restored to the state where it was? Or just some directories?

How about MySQL databases, can they also be backup'd this way or should some other tool be used?

If my HD then fails, would the restorartion to the new HD be just: 1) install Ubuntu 2) copy all directories from the backup drive to the new drive??

---

