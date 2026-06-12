---
title: "Cannot Save Mount Information on live cd"
date: 2007-02-11
forum: General Help
---

### Post by acaby on 2007-02-11
I searched for this and could not find any results. I hope I did not miss anything. Anyway is there a way to copy the mount information onto the live cd. (Mine is a CD-RW)I have been using windows since DOS and they are just making too many changes to suit me. Time to get out.I have been working feverishly with Ubuntu 6.10 for almost 2 day's and finally got the HDD Mounting down pat but every time I turn off my computor and Boot up again from the live CD I have to do it all over again. Gets Old after awhile but I will have to live with it for now if that is the way it is. I cannot load in on my hd yet - Only got 5.5 gigs and been cleaning to get more space but it is a chore. 
Any suggestions appreciated
Thanks,
Arthur

---

### Post by acaby on 2007-02-11
I searched by keyword "mount" and I think I found the problem. New at this so please forgive.
Arthur

---

### Post by acaby on 2007-02-12
> **acaby said:**
> I searched by keyword "mount" and I think I found the problem. New at this so please forgive.
Arthur

Well I guess I spoke too soon. I did not correct the problem. I went to [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
and did EXACTLY as suggested in those instructions for a vfat hda1 partition. mkdir /windows, assigned dev/hda1 to as per instructions. When I shut down and went to bed it was working perfectly. I even pointed Firefox download manager to HD Partition, Downloaded a few files -- Worked fine.

When I booted up this AM it was the same problem????  No HD Partition recognized, The windows dir was gone.
The line I added to /etc/fstab did not even save. 

So I did the routine all over AGAIN. Worked Fine. I am back on the forum from Win98 now. Until I can free up enough HD space to install Ubuntu and **try and learn **it from there I am finished. **This live CD problem is giving me a migrane.** 
Thanks
Arthur

---

