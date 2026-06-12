---
title: "Combining External Discs: Raid? LVM? Something completly different?"
date: 2014-09-11
forum: General Help
---

### Post by AllesMeins on 2014-09-11
I have four USB-Discs at my disposal. I need to combine the available space of (at least) two of them but want to keep a reasonable level of data security. I was wondering what tools to use. Lately I've been reading a lot about diffrent RAID-Types and LVM and it seems to me that both have a lot of dangers to lose all your data with one wrong command or just bad luck (at least I've seen many posts with people asking for help because of complete data loss). And with external hard drives i guess I have to account for the fact that a cable might become loose, an USB-Port might die or even a kernel/system failure might kill the connection to one or more of my drives. 

So is there a solution that combines the space of (at least) two disks, can recover easily after one (or multiple discs) get disconnected and still ensures data security if one disc should suffer critical damage? What would you advise? RAID? LVM? Combining the two? Something completly different that I'm not aware of?

---

### Post by bab1 on 2014-09-11
> **AllesMeins said:**
> I have four USB-Discs at my disposal. I need to combine the available space of (at least) two of them but want to keep a reasonable level of data security. I was wondering what tools to use. Lately I've been reading a lot about diffrent RAID-Types and LVM and it seems to me that both have a lot of dangers to lose all your data with one wrong command or just bad luck (at least I've seen many posts with people asking for help because of complete data loss). And with external hard drives i guess I have to account for the fact that a cable might become loose, an USB-Port might die or even a kernel/system failure might kill the connection to one or more of my drives. 

So is there a solution that combines the space of (at least) two disks, can recover easily after one (or multiple discs) get disconnected and still ensures data security if one disc should suffer critical damage? What would you advise? RAID? LVM? Combining the two? Something completly different that I'm not aware of?

[CENTER]**[SIZE=4][COLOR="#800080"]*** For Data Security Always Backup Your Data ***[/COLOR][/SIZE]**[/CENTER]

Neither RAID or LVM will provide the security you expect!  RAID is not a data secure plan at all.  It is for high availability of  a system (e.g.  A disk drops out and the system continues on).  Rebuilding an array with modern large capacity can be extremely time consuming it not impossible considering the errors that can occur during rebuilding.  Linux LVM is good for assembling and removing disks of various capacities in one data volume.  But, it also suffers from recovery time and reliablity problems.

In short neither of these methods of disk abstraction create data security or are particularly fast in reconstitution after a disk failure.

**BACKUP YOUR DATA!**  This is the only way to assure your data is secure against disk failure.  

How you utilize your disk capacity is more a matter of how you want to use your resources.  

Do you have an application that just has to run 24/7 or is mission critical?  Then use RAID5 or 6.  If you loose a disk you can *schedule * your downtime for replacement and restore from backups with no data loss. 

Do you have a bunch of dissimilar disks or a need for capacity that can span all the disks you have?  Then use LVM to build one large volume.  If a disk fails in the future you can recreate the volume and restore from backups with no data loss.  One nice feature is you can create snapshots of the entire volume and save them as backups.

Either way:  **You need RELIABLE BACKUPS ON A REGULAR BASIS for data security**.

---

