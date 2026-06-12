---
title: "Raid fails after reboot for power outage: no md superblock detected."
date: 2013-07-18
forum: General Help
---

### Post by quickk on 2013-07-18
Hi, 

    I have a raid 10 array in my desktop machine.   I had to reboot it with the "reset" button because of what apparently was some sort of crash (screens were black an unresponsive), and so the machine didn't shut down properly.   Now when I reboot it, I get a message asking me if I want to start the raid array in degraded mode.   

I now get the following:

```
cat /proc/mdstat
Personalities : [raid10] [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] 
md0 : active raid10 sdb1[1] sda1[0]
      4395197952 blocks super 1.2 512K chunks 2 far-copies [3/2] [UU_]

```

so it looks like drive 3 is dropped.   However, there appears to be no problems with this drive based on the reported SMART self test data.   Examining the raid array, I get:
```
sudo mdadm --examine /dev/md0 
mdadm: No md superblock detected on /dev/md0.

```   

What's going on?

---

### Post by TheFu on 2013-07-18
md thinks 1 of the disks isn't in the array so it isn't using it. You need to tell it to re-assemble adding the 3rd disk back in. Of course, double check that the cables are all seated properly and that the OS sees all the drives just fine.  Something like this:
**sudo mdadm /dev/md0 -a /dev/sdc1**
will be needed.  If that command completes, follow the parity rebuild with 
**cat /proc/mdstat**

If the 1st command failed, RTFM for mdadm to see other corrective steps you can take.

Depending on the size of the array, it can take a few hours to multiple days to rebuild everything.  Performance will probably suffer during this, so I wouldn't start until after a production day end. Also, I'd be very certain that my backups were excellent, as rebuilding parity can cause other disks in the array to fail ... in theory, the likelihood of failure goes up where there's an 80% chance of another disk failing during the rebuild.  I think the MTBF data used for that estimate was flawed, but it is something to consider.

---

### Post by SaturnusDJ on 2013-07-19
The --examine flag for mdadm is only to be applied at array members (/dev/sd..). Superblocks are stored at array members, not at the array (/dev/md..) as it is.
Array information can be obtained using ```
mdadm --detail /dev/md..
```


The add option suggested by TheFu should work.
But, what I would try first are these options:

1. If no data is changed, a re-add might be used to omit the resync.

2. Stop the array and try to assemble it given all members manually.
```
mdadm --assemble /dev/md0 /dev/sd[a-c]1
```
I'm not recommending the use of the force flag here to prevent possible, minimal data loss.

---

### Post by quickk on 2013-08-01
Thanks for the advice everyone.   Simply trying to add the disk back wouldn't work.   What I ended up doing was to create a new partition table, partition and reformat the disk that was causing me trouble.   I first ran some disk diagnostics, and the disk seemed fine.   

Now, adding the disk worked and the array is rebuilding with this disk.   So what I did was (after reformat and all):
```
 sudo mdadm /dev/md0 -a /dev/sdc1
```
where /dev/sdc1 is the partition that I wanted to re-add to the array.

---

