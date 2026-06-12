---
title: "Recover Data from LVM Volume"
date: 2007-12-12
forum: General Help
---

### Post by TTT_travis on 2007-12-12
So... I always said someday I was gonna backup my personal server for multimedia etc. but I just seemed to never get around to that...and now it might be too late.

Here's the deal: my server has 3 drives the first drive is just a small drive formatted with ext3 and contains the main operating system. The second and third drives (320GB and 500GB) are used for actual storing of music, media etc.

My tragic story began yesterday, it was like any other day -- I go up, went to school, came home and it was at this point my life changed forever. There was a small package on my door step, it was a small box brown box delivered by UPS. I pondered what might be inside it for a few seconds, then proceeded to tearing it open like a wild animal. Inside I discovered my new cheapo 320GB SATA drive I had ordered. 

--NOW ONTO MY ACTUAL PROBLEM--

I put the drive into my server, formatted it, and added it to my LVM group, after I did LV Extend it still showed up as only having 30GB of free space, even though it should be closer to 300gbish now that I added the new drive. Like any computer problem I began to trouble shoot and somehow ended up removing my Logical volume (called data).

I have a volume group called: Server
with 3 physical volumes (500GB Sata, 320GB PATA and the new 320GB SATA)
and a logical volume called data
fstab mounts /dev/server/data to /data on boot and it normally worked perfectly. But after accidently deleting root I continued to mess around to try to get it working, even trying to re-add the root lv.

At this point I cannot mount root like I normally would, says it won't mount and acts like it's not formatted.

The two original drives that I used for data still have partitions on them in the format LVM2 MEMBER

I cannot get these to mount anyway (suppose because they're LVM members) and I am afraid to try to many things incase the data is still there somehow.

How do I go about seeing if the LVM drives still have any data on them!

Thanks in advanced for anyone willing to help out, this is really important that I get this working soon!

---

