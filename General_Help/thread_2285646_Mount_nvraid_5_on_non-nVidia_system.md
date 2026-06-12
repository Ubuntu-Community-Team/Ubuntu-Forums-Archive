---
title: "Mount nvraid 5 on non-nVidia system"
date: 2015-07-07
forum: General Help
---

### Post by Isaac_Brown on 2015-07-07
I had an old EVGA SLI 680i motherboard with two, 3-drive nvRAID 5 sets running on it with **NTFS** file systems. The motherboard has died, but I have an ASRock motherboard with an LGA 775, so I'd like to use it to recover important data from the nvraid 5 sets. I have no reason to believe the RAID is damaged in any way, I'm sure if I had another nVidia mobo it would boot right up. The goal is to recover the data on one RAID set to available storage space, then redeploy the disks as a new non-hardware dependent RAID 5 to use as storage to recover the second set of disks. 

I guess the first question is, is it possible to mount an NTFS nvRAID 5 in ubuntu on a non-nVidia motherboard?
The follow-up is, of course, how?

The next question is, is there a software RAID solution that is compatible with Linux and Windows 7/10 (I'd like to use the storage in both environments)?

I did dig up this post and have yet to try it:
[https://www.linuxquestions.org/questions/linux-newbie-8/dmraid-is-there-a-live-linux-distro-that-can-mount-a-fakeraid-array-858439/](https://www.linuxquestions.org/questions/linux-newbie-8/dmraid-is-there-a-live-linux-distro-that-can-mount-a-fakeraid-array-858439/)
I thought there might have been some advancement/changes in the intervening years

---

### Post by dino99 on 2015-07-07
related thread [http://ubuntuforums.org/showthread.php?t=1442326](http://ubuntuforums.org/showthread.php?t=1442326)
but you should get better answers on the nvidia support  [http://nvidia.custhelp.com/app/answers/detail/a_id/781/~/setting-up-nvraid](http://nvidia.custhelp.com/app/answers/detail/a_id/781/~/setting-up-nvraid)

---

### Post by Isaac_Brown on 2015-07-07
I just wanted to update this with the "solution" aka, it just worked. I simply connected the drives to the mobo and using a live USB of 12.04, the file browser mounted the nvRAID 5 like it was a completely normal thing without any terminal commands or anything. The motherboard is the ASRock G31M-GS R2.0 (which has the Intel G31 northbridge and ICH7 southbridge, so decidedly not nVidia or nvRAID compatible). I have to say, I'm super impressed, since it sounds like just a few versions prior I would have had to fiddle around with dmraid and whatnot.

Now my biggest issue is having 6 drives on a mobo with only 4 SATA connections. It will end in me forgetting to save something important before splitting up one of the RAIDs and then hoarding two drives for years and years becuase I will need them one day, but never actually using them. That or I'll blow a bunch of money on a skylake system that ends up being a glorified media server like this rig was.

---

