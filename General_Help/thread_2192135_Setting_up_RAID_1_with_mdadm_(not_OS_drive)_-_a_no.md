---
title: "Setting up RAID 1 with mdadm (not OS drive) - a novice's queries"
date: 2013-12-06
forum: General Help
---

### Post by bruce-law on 2013-12-06
I'm attempting to set up a simple software RAID set-up on my HP microserver. I have Ubuntu 12.04 installed on a SSD, with 2 x 2TB drives for media files (video, music, etc.), plus some other unimportant drives (old installs, miscellaneous files).
 
I'm using the 2 x 2TB drives (devices sdb & sdc) to create a RAID 1 array. I am creating one partition on each of those drives.

However, one of those 2 media drives was already half-full when I bought the 2nd drive. So I'm trying to *migrate* (not sure if that's the correct term) the files from the 1st drive on to a RAID array across both drives. Another way of putting it is that I'm converting an existing drive into an array.

I did this by loosely following [this guide]("https://wiki.archlinux.org/index.php/Convert_a_single_drive_system_to_RAID"), missing out the bits about the swap partition and grub. Basically, I copied the files from the old drive (sdb) to the new drive (sdc) which I had partitioned as a RAID device and set up with mdadm as device md0. Then I re-partitioned the old drive (sdb) and added to the array and allowed them to rebuild the files.

I thought I had a handle on this, having tinkered around on Ubuntu for a couple of years, and all seemed well. But now I'm not sure my array is correctly set up.

Firstly, if I look at Disk Utility I see this:

[IMG][[IMG]http://i1215.photobucket.com/albums/cc508/pulck/Screenshotfrom2013-12-05211717.png[/IMG]]("http://s1215.photobucket.com/user/pulck/media/Screenshotfrom2013-12-05211717.png.html")[/IMG]

Why is it showing 2 arrays under 'Multi-disk devices' and why is one of them not running?

Second, if I type this into terminal:

```
sudo mdadm --examine /dev/sd* | grep -E "(^\/dev|UUID)"
```

I get this:

```
mdadm: No md superblock detected on /dev/sda1.
mdadm: No md superblock detected on /dev/sda3.
mdadm: No md superblock detected on /dev/sda4.
mdadm: No md superblock detected on /dev/sda5.
mdadm: No md superblock detected on /dev/sdb1.
mdadm: No md superblock detected on /dev/sdc1.
mdadm: No md superblock detected on /dev/sdd3.
mdadm: No md superblock detected on /dev/sdd4.
mdadm: No md superblock detected on /dev/sdd5.
mdadm: No md superblock detected on /dev/sdd6.
/dev/sda:
/dev/sda2:
/dev/sdb:
     Array UUID : 17140c98:5bfcabe3:a7435d1c:fb26961b
    Device UUID : ed391ef0:26d1ba56:273e2640:4925e0d0
/dev/sdc:
     Array UUID : 17140c98:5bfcabe3:a7435d1c:fb26961b
    Device UUID : d735d1d4:fce9144c:7645d3b3:3ca20217
/dev/sdd:
/dev/sdd1:
/dev/sdd2:
/dev/sde:
/dev/sde1:

```

Shouldn't I have superblocks on sdb and sdc?

Any ideas what I might have done wrong? Do I need to move all the files off these drives and start again from scratch? I have the option to do this, as I have a large external drive which I can move the files to.

Any help massively appreciated.

---

### Post by SaturnusDJ on 2013-12-07
Post:
```
cat /proc/mdstat
```

Then look at the array, post the output for the md device (most likely md0):
```
mdadm --detail /dev/md0
```

Also look at the array members and post the output for them as so:
```
mdadm --examine /dev/sdb1
```

---

### Post by bruce-law on 2013-12-07
Thanks for your reply. Here are my posts.

> **SaturnusDJ said:**
> Post:
```
cat /proc/mdstat
```

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] md0 : active raid1 sdc[3] sdb[2]
      1953383360 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>



```



> **SaturnusDJ said:**
> Then look at the array, post the output for the md device (most likely md0):
```
mdadm --detail /dev/md0
```

```
/dev/md0:
     Version : 1.2
  Creation Time : Mon Nov 18 23:34:22 2013
     Raid Level : raid1
     Array Size : 1953383360 (1862.89 GiB 2000.26 GB)
  Used Dev Size : 1953383360 (1862.89 GiB 2000.26 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent


    Update Time : Sat Dec  7 23:48:34 2013
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


           Name : behemoth:0  (local to host behemoth)
           UUID : 17140c98:5bfcabe3:a7435d1c:fb26961b
         Events : 49517


    Number   Major   Minor   RaidDevice State
       3       8       32        0      active sync   /dev/sdc
       2       8       16        1      active sync   /dev/sdb
brucie@behemoth:~$ 

```





> **SaturnusDJ said:**
> Also look at the array members and post the output for them as so:
```
mdadm --examine /dev/sdb1
```

```
mdadm: No md superblock detected on /dev/sdb1.
```

and

```
mdadm: No md superblock detected on /dev/sdc1.
```
Does that throw any light on things?

---

### Post by SaturnusDJ on 2013-12-08
You have an array based on devices. This will work but is not the most smart setup. Reason can be read here: [http://ubuntuforums.org/showpost.php...73&postcount=8](http://ubuntuforums.org/showpost.php...73&postcount=8)

```
mdadm --examine /dev/sdb
mdadm --examine /dev/sdc

```
That should bring up the proper examines.

---

### Post by bruce-law on 2013-12-08
Thanks, that's very helpful.

Would you mind posting that link again? It doesn't seem to work.

Will I have to start the array from scratch again, or can I migrate over to a partiton based array?

---

### Post by SaturnusDJ on 2013-12-08
[http://ubuntuforums.org/showthread.php?t=2110658&p=12484473#post12484473](http://ubuntuforums.org/showthread.php?t=2110658&p=12484473#post12484473)

You can do what you probably did when you built the current array. Start the array degraded with one member. If you think it's worth it because that of course isn't without risk.

---

### Post by bruce-law on 2013-12-08
Thanks for your help. I'll copy the files to an external drive first, for safety.

---

