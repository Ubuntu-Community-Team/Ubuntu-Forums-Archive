---
title: "advice on a partiton / filesystem scheme?"
date: 2007-03-23
forum: General Help
---

### Post by yellowband on 2007-03-23
Hi

I'm looking for some advice, on how you guys logically set up your hard drives to store media.  I have 4+ drives, and i'm finding it annoying to have multiple directories for, say, movies, or tv shows. I would like to have one giant partition with one root folder, and the have a movies, tv, music folders under that. This way i only have to share one folder on the network and configuring media front ends will be easier.  

is it advisable to have a single partition spread over multiple drives?  is there another soltuion?  

thanks for any help.

---

### Post by Muzik83 on 2007-03-23
Hey,

It all depends on how much you're willing to lose!

RAID is probably your safest option, if you mirror and stripe it then if you lose a drive you can swap a new one in without any loss of data.  However raid is expensive (since you need more disk for the redundancy).

For my media, I use Logical Volumes, which allow you to stick multiple drives in a single "VolumeGroup", then create "Logical Volumes" (partitions) on that gigantic volume group.  In your case it sounds like you want to create one gigantic logical volume, the size of the VG.

The problem with this is if one single drive fails, you quite probably will lose all your media on all your drives!  For this reason, I only trust my movies and such on the non-mirrored LVM -- if I lost it all I would be sad, but not suicidal (the way I would be if I lost my /home/ directory with thousands of hours of work inside it).  LVMs are neat though, because you can resize the partitions without rebooting/losing data. 

-sean

---

### Post by yellowband on 2007-03-23
logical volumes eh... cool thanks!

i'm not too concerned with safety. This will be puerly a media PC and all of it will be backed up on dvd.  Any good tutorials  you used to set up logical volumes?  

Is this logical volume a layer above the hard drive partitions themselves?

---

