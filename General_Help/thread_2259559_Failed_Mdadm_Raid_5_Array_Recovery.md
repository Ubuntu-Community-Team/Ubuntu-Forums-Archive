---
title: "Failed Mdadm Raid 5 Array Recovery"
date: 2015-01-05
forum: General Help
---

### Post by Seaweed on 2015-01-05
My setup is as follows

/dev/sdb/ 
/dev/sdc/ 
/dev/sdd/ 
/dev/sdf/

I have the following 4 1.5TB drives in a mdadm raid 5 array. One of the disks (sdb) died on me leading the array to start up running in degraded mode.

No problem I thought as this is the whole reason I setup a raid 5 array in the first place. I had a spare blank 1.5tb disk to replace the dead sdb disk, so I formatted it and added it into the array. However this is where the problem really starts.

When recovering the array after adding a fresh disk the recovery fails every single time, though not always at the same percentage in /proc/mdstat. After recovery fails /dev/sdc is marked as a failed device and is also removed from the array, though it can be forced to be added again.

Here's some of the outputs from syslog

```

Jan  5 01:16:28 serverlol kernel: [11303.917452] md/raid:md0: Disk failure on sdc1, disabling device.
Jan  5 01:16:28 serverlol mdadm[3345]: Fail event detected on md device /dev/md0, component device /dev/sdc1

```

Here's the output of syslog when the failure occurs whilst recovering the raid

```
Jan  5 01:16:24 serverlol kernel: [11300.853422] end_request: I/O error, dev sdc, sector 693768801
Jan  5 01:16:24 serverlol kernel: [11300.853426] md/raid:md0: read error not correctable (sector 693766752 on sdc1).
Jan  5 01:16:24 serverlol kernel: [11300.853429] md/raid:md0: read error not correctable (sector 693766760 on sdc1).
Jan  5 01:16:24 serverlol kernel: [11300.853432] md/raid:md0: read error not correctable (sector 693766768 on sdc1).
Jan  5 01:16:24 serverlol kernel: [11300.853434] md/raid:md0: read error not correctable (sector 693766776 on sdc1).
Jan  5 01:16:24 serverlol kernel: [11300.853436] md/raid:md0: read error not correctable (sector 693766784 on sdc1).
Jan  5 01:16:24 serverlol kernel: [11300.853438] md/raid:md0: read error not correctable (sector 693766792 on sdc1).
Jan  5 01:16:24 serverlol kernel: [11300.853441] md/raid:md0: read error not correctable (sector 693766800 on sdc1).
Jan  5 01:16:24 serverlol kernel: [11300.853443] md/raid:md0: read error not correctable (sector 693766808 on sdc1).
Jan  5 01:16:24 serverlol kernel: [11300.853446] md/raid:md0: read error not correctable (sector 693766816 on sdc1).
Jan  5 01:16:24 serverlol kernel: [11300.853448] md/raid:md0: read error not correctable (sector 693766824 on sdc1).
```

I have run smartctl on /dev/sdc and I see that there are definitely some errors, I'm running the same tests on the remaining drives in the array but it takes a very long time to complete on drives this big. I also unmounted the array and ran fsck on it whilst it was running in its degraded state. 

Ok so here are the recovery steps I have taken so far, I have ordered an external 4tb hard disk onto which I intend to back up as much data as I possibly can from the degraded array (total amount of data is 3.2tb). This is because the array can still be mounted and browsed whilst running in degraded mode. Though of course presumably this will not be the case for all of the files contained on it.

I have currently stopped mdadm and unmounted the array whilst I wait for the 4tb backup disk to arrive.

My plan at the moment is to use the tool "safecopy" to copy as much data as I can to the external hard drive. Is this the best way to do it? Will this give me a list of any files that can't be copied due to errors? Given that I have no more 1.5tb drives to try mirroring the sdc onto. Is this the best utility to copy the data from my degraded /dev/md0 device? Is there anything more I can do to minimize my data loss? Alternately is there a way I can still add a 4th drive back into the array whilst ignoring the sector errors on /dev/sdc? 

I had a replacement disk for the first initial failed drive (sdb) but I do not have any more 1.5 tb drives to replace the other one being marked as failed (sdc). This is why I just want to recover as much data as I possibly can to the external drive, after that I will probably just build an entirely new array since these 1.5TB drives are very old. 

Any advise would be much appreciated, I am really worried about my data at the moment :(

---

### Post by Seaweed on 2015-01-05
Seems I missunderstood how safecopy works, I don't really want to make an image of the entire raid array or a drive, I just want to try and copy every file I can from the degraded array to the external drive and skip the ones that can't be read.

Is there a better way of doing this? Can I use rsync or something to do the copying and just skip a file if it has an error because of a bad sector, or is mdadm just going to hang the OS every time it tries to read a bad sector? 

At this point I have no intention of keeping this array I just need to get as much of the data as I can off of it.

Everything I'm reading says ddrescue is the way to go, but I don't like this option because I don't have any spare 1.5tb hard drives to mirror /dev/sdc onto and can't find one for purchase. I was under the impression all drives in a raid 5 array must be the same size. Could I in theory buy a new 2tb drive and partition it to 1.5tb and then use ddrescue? I would still like to avoid this if I can, because I have no faith in the remaining drives in the array (though they do pass smart checks) and I would rather get all the data I can off now and make a brand new array with all new hard disks than have to gradually remove them one at a time from the current array. 

Finally I have also read I can manually fix the problem sectors on the drive which will force mdadm to suceed in the resync of the array, obviously this is not something I want to undertake lightly and would appreciate any advise people can give regarding this article [http://www.sj-vs.net/forcing-a-hard-disk-to-reallocate-bad-sectors/](http://www.sj-vs.net/forcing-a-hard-disk-to-reallocate-bad-sectors/) because on paper it sounds like it could solve all my problems, do you think this solution could apply in my case?

---

