---
title: "RAID1: cannot replace faulty spare (is marked again as 'faulty spare' within seconds)"
date: 2013-11-07
forum: General Help
---

### Post by manucubus on 2013-11-07
I got a problem that I cannot solve: Our fileserver runs XUbuntu and 3 RAID1s. One has a problem since monday: it consists of sdb and sdc. sdb was marked as faulty by mdadm for unknown reasons. I used --remove to remove it from the RAID and then to add it by --add. All was fine, re-syncing started but never got above 0% and after a few seconds, sdb was again marked as 'faulty spare' (and therefore the RAID degraded, but clean).
So I saved the first 512 byte of the old sdb to a file, bought a new HDD of same size (4TB), shut down the computer and replaced sdb physically, switched the computer back on and wrote the 512 byte back to the new drive to have the same partition info as the old drive (both are the same type, from same company). But the new drive shows the same behaviour as the old: I can add, re-syncing starts and after a few seconds its marked as 'faulty spare'.
Here exactly what i did:
[B]
mdadm --remove /dev/md/1 /dev/sdb
maadm --detail /dev/md/1[/B] gives me:

/dev/md/1:
        Version : 1.2
  Creation Time : Sat Jun  8 22:32:05 2013
     Raid Level : raid1
     Array Size : 3906887360 (3725.90 GiB 4000.65 GB)
  Used Dev Size : 3906887360 (3725.90 GiB 4000.65 GB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent

    Update Time : Thu Nov  7 06:56:13 2013
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           Name : File-Server:1  (local to host File-Server)
           UUID : 44ed561f:b733e946:e69820f4:aba9b223
         Events : 2424

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       32        1      active sync   /dev/sdc

[B] mdadm --add /dev/md/1 /dev/sdb
**maadm --detail /dev/md/1** [/B]gives me:


        Version : 1.2
  Creation Time : Sat Jun  8 22:32:05 2013
     Raid Level : raid1
     Array Size : 3906887360 (3725.90 GiB 4000.65 GB)
  Used Dev Size : 3906887360 (3725.90 GiB 4000.65 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Thu Nov  7 06:57:49 2013
          State : clean, degraded, recovering
 Active Devices : 1
Working Devices : 1
 Failed Devices : 1
  Spare Devices : 0

 Rebuild Status : 0% complete

           Name : File-Server:1  (local to host File-Server)
           UUID : 44ed561f:b733e946:e69820f4:aba9b223
         Events : 2431

    Number   Major   Minor   RaidDevice State
       2       8       16        0      faulty spare rebuilding   /dev/sdb
       1       8       32        1      active sync   /dev/sdc

and after a few seconds:
/dev/md/1:
        Version : 1.2
  Creation Time : Sat Jun  8 22:32:05 2013
     Raid Level : raid1
     Array Size : 3906887360 (3725.90 GiB 4000.65 GB)
  Used Dev Size : 3906887360 (3725.90 GiB 4000.65 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Thu Nov  7 06:57:50 2013
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 1
  Spare Devices : 0

           Name : File-Server:1  (local to host File-Server)
           UUID : 44ed561f:b733e946:e69820f4:aba9b223
         Events : 2436

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       32        1      active sync   /dev/sdc
       2       8       16        -      faulty spare   /dev/sdb


same behaviour if I zero the superblock (**mdadm --zero-superblock /dev/sdb**) before adding sdb.
I do all commands as root and the system holds 3 more 4TB drives, ie the mainboard can handle them. The old harddrive was checked for errors using badblocks, but all is fine.

Does anybody have any idea, what the problem is?

---

### Post by XBNCPRk on 2013-11-07
After physically replacing the faulty drive, wouldnt you want to copy the partition table from the old good one, not the old faulty one?

---

### Post by manucubus on 2013-11-07
good point. I just tried to copy the first 512 bytes from sdc (the second drive in the raid) over to the new sdb but this doesnt change anything - sdb is again marked as faulty spare within seconds :(

---

### Post by XBNCPRk on 2013-11-07
When you first had the problem with sdb, did you mark it as failed before you removed it from the array? (...and for anyone that comes across this later, never use --fail with a raid0 or linear array).

---

### Post by manucubus on 2013-11-07
it was already marked as failed by the system, so I didnt mark it again  manually. But I think I wouldnt be able to --remove /dev/sdb if its not  marked as failed, right?
What would be the consequence of removing a non-failed drive?

---

### Post by XBNCPRk on 2013-11-07
Yes, it should have already been marked as failed by the system, but my gut is telling me that its seeing the new disk as the same as the old, and rejecting it because it already thinks its bad. Anyone know if its possible that the old failed drives UUID got copied to the new one along with the superblock copying, and its being marked as faulty because its been blacklisted by mdadm?

---

### Post by manucubus on 2013-11-07
interesting idea and it could explain alot.
In the meantime i took the original (old) HDD, created a fresh GPT on it (it in a different computer), put it back into our fileserver, didnt try to write the first 512 byte but left it untouched adding it to the raid works fine now! The RAID is being rebuild and all looks fine.

I think my mistake was that I wrote the 512 back on the new drive - this seemed to cause all the problems...
Thanks alot for the help - I think I learned alot :)

---

### Post by XBNCPRk on 2013-11-07
Glad to hear its workin for you... also, a format will change the drives UUID, so that may have been part of the problem.

Did you ever figure out what kicked the drive from the array in the first place?

---

### Post by manucubus on 2013-11-08
yes, i also came to believe that I accidently copied the UUID over to the new drive causing all the problems with the new drive.
But  I have no idea why the original drive was kicked out in the first  place...the fileserver draws its power from an uninterrupted power  supply with line filter, so no surge or brownout could have upset the  electronics. Probably it will always stay a mystery.
Thanks again for your help - your point about the UUID really helped me understand some of the problems :)

---

