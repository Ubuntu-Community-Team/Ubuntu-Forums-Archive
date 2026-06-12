---
title: "mdadm won't mount Raid 1 disk - bad superblock"
date: 2013-06-26
forum: General Help
---

### Post by fharrington on 2013-06-26
Hi All, here's my situation: 

Had a 2-bay Synology Diskstation with 2 x 2TB drives.  Synology uses mdadm to store files, in this case Raid1. 

The box crashed and array was damaged somehow. Drive's showed errors as well (ATA).

ddrescued one of the drives to a new health 2TB drive, tried to reassemble, mdadm reports bad superblock. (same as when trying with original disks)

So as of right now I'm scanning for Superblocks with PhotoRec(testdisk).

My first question is: will testdisk be able to recover files from the non-assembled/mounted mdadm array? Can it even see those files without a /dev/mdX to scan?

Second question - assuming it recovers a backup Superblock, how can I use that to get the raid back up?

Thanks in advance!

Fletcher

---

### Post by TheFu on 2013-06-26
Every time I've had an mdadm array fail, I just put in a new HDD to replace the failed disk and told the array to assemble. That would have the RAID rebuild itself over the next 2-24 hours.  If you ddrescued the wrong disk (the one that didn't fail), then the disk array sees (2) 100% identical disks and doesn't know which is which. In RAID1, there is an A and a B disk internally even if we don't know which is which. The disks are not 100% mirrored. There are logical differences to help mdadm out.

You've probably heard this before, but **RAID is not a backup** [https://www.google.com/search?client=ubuntu&channel=fs&q=raid+is+not+a+backup&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=raid+is+not+a+backup&ie=utf-8&oe=utf-8).  RAID is for HA needs, High Availability, not backups. Backups are still necessary.

I wish you luck with your data.

---

### Post by SaturnusDJ on 2013-06-26
I've mounted mdadm RAID1 members without the array being assembled.
In other words: (Sometimes) it is possible to mount a mdadm RAID1 member as single non-RAID disk.
Maybe it will help you.

Remember that, once mounted as single read-write disk, it is out of sync with the other member(s).

---

### Post by fharrington on 2013-06-26
Hi TheFu, both drives of the original RAID 1 array have the same issues, so there's no "good" disk. We were using this for high availability, not a sole backup.  It is a way to have data onsite and quickly accessible if the user's copy becomes compromised.  We have offsite, etc. That being said, two users did not heed my notice that this should be a redundant location only and used it as the primary location for a couple files.. so I'm trying to recover those.

Any other input is much appreciated!

---

### Post by fharrington on 2013-06-26
Hi SaturnusDJ, I did attempt this earlier on, it allowed me to see the files that formed the OS of the device but the point where the data started; "/volume1/" is empty when mounted normally.  Thanks for the idea though!

---

### Post by SaturnusDJ on 2013-06-27
LVM maybe?

Can you post partition layout?

---

### Post by fharrington on 2013-06-27
You are exactly right Saturnus.  Looks like the mdadm raid uses LVM for the "data portion".. not that I really know what that means :)  I installed LVM2 on the maintenance system with old an new HD's attached. I used "lvm lvscan" but it sees nothing.  I'm running of a live USB with no persistence so I hope it's not wanting a reboot. Is there any way LVM could be missing an existing LV?  Is there a way to tell it to "force" it?

Here is the latest suggestion from Synology support along with the partition info you asked for.

[FONT=arial]Try running:
[/FONT]
[FONT=arial]lvm lvscan[/FONT]
[FONT=arial]# it should say something like "inactive '/dev/vg1000/lv' [7.26 TB] inherit"[/FONT]

[FONT=arial]vgchange -ay /dev/vg1000/lv #Correct the vg1000/lv with the one you got from lvmscan[/FONT]

[FONT=arial]#Then try mounting the result from lvm scan to volume1

The partitions are:

/dev/sda1-5  - [/FONT][FONT=arial]The ddrescued copy of sdc. [/FONT][FONT=arial]
/dev/sdbX - The ubuntu live usb
/dev/sdc1-5 - [/FONT][FONT=arial]One of the old damaged RAID 1 drives[/FONT][FONT=arial]
/dev/md2p1 - The forced mdadm volume 
/nas/  -  the mount point for md2p1
/nas/volume1/ - the place where all the data should be (where the LV gets mounted?  or is this the LV?)
[/FONT]

---

### Post by SaturnusDJ on 2013-06-27
Mdadm doesn't do LVM. ;)
Synology controlled the layers.

That should work yes.

Run these commands, elevated (so sudo):
```
partprobe
```
```
vgscan
```
```
vgchange -ay
```

If it's LVM, you should be able to mount a partition that became available at /dev/mapper/.

For correct partitions on the drive run this command:
```

parted /dev/sda print

```

---

### Post by fharrington on 2013-06-27
here is the vgscan output.  

```
root@ubuntu:/# partprobe
root@ubuntu:/# vgscan
  Reading all physical volumes.  This may take a while...
  /dev/sdc5: read failed after 0 of 4096 at 4096: Input/output error
  No volume groups found
root@ubuntu:/# vgchange -ay
  No volume groups found
```


*please note that i changed my previous post to reflect the correct drive info (sdC was old raid 1 drive, sdA is ddrescued new healthy drive)

---

### Post by fharrington on 2013-06-27
just a thought Saturn, if the superblock was bad on the original raid 1 drive and ddrescue made a "block for block" copy of it, wouldn't I still have a bad superblock? Since it holds the metadata could this be the reason i had to force mdadm to mount (assume-clean etc) and the reason lvm doesn't see an vm's?  Would restoring from a backup superblock potentially fix these issues?  I'm grasping at straws here, just an idea ;)

---

### Post by TheFu on 2013-06-27
Well, that just sucks.  I've lost data using LVM too - about 80% of my data a decade ago. I was stupid and extended a volume across multiple disks ... sorta like RAID0. 1 of the disks failed and I was unable to figure out how to recover any files off the other 2 drives. After a few months (it was a very busy time), I stopped looking for answers, gave up, formatted the drives and moved on.  Some of those home movies were priceless.

That was THE event that taught me **backup religion**.

I truly hope you have better luck that I. I'll be lurking and will ahve my fingers crossed.

---

### Post by SaturnusDJ on 2013-06-27
Superblock is probably still bad yes. Although, sometimes ddrescue it a solution because it really tries to read the data of the disk instead of giving up as easy as other copy tools.
But, in my opinion the whole mdadm/raid part doesn't matter much because, as said earlier, mdadm RAID1 members are mountable as single disk...that's my (tested) experience at least.
As there is still a little chance this is not (always) true, there is the option of doing a recreate. This is a last resort however because it might do more damage than good. We'll not do a recreate at this moment.


How to continue now...
Please provide more information. Maybe that will bring something up that's useable to help you.

Do these commands bring something up?
```
mdadm --examine /dev/sd*
```

Run the parted command for **every** disk/array:
```
parted /dev/sda print
```

Also, let's have a look at the S.M.A.R.T. data. Run this for at least the corrupted disks:
```
smartmontools -a /dev/sda
```


@TheFu
Totally true. Everyone not making backups just have to loose it once before they're convinced. It happened to me too.

---

### Post by fharrington on 2013-06-28
Saturnus and Fu, thanks for your help with this issue.. data has returned!  After receiving my replacement NAS I put one of the old damaged HDDs back in with the ddrescued new HDD and it was able to see the data on the new disk.  Guess the Synology distro/firmware had the tools needed to see the volume/mount it... would have been nice if we had a clear answer as to how to do this outside of the device but I can't complain at this point. :)  Thanks again guys!

---

