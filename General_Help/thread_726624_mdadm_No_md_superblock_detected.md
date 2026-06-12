---
title: "mdadm: No md superblock detected"
date: 2008-03-16
forum: General Help
---

### Post by SilkBC on 2008-03-16
Hi There,

I recently performed a bit of a b0rked RAID1 mirror setup on a live system (I booted from a Knoppix CD and did it through that).  I had created a '/dev/md0' and '/dev/md1' consisting of the following:

  md0:
    /dev/sda1
    /dev/sdb1

  md1:
    /dev/sda2
    /dev/sdb2

Of course I made no backup ahead of time.

I wasn't able to boot the system, and ended up performing a re-install on one of the drives (/dev/sda).  I had to "fail" the partitions from their respective RAID mirrors then remove them in order to perform the re-install.  The other drive had it's partitions left in tact, though apparently still part of the RAIDs.

The partition that was part of the '/dev/md1' contained a virtual machine (VMDK files and such).  When I re-installed the OS, I left the '/dev/sda2' partiton untouched and was happy to see the virtual machine files on there still.

When I booted the virtual machine, however, it could not boot as it could not find any files. In fact, the virtual disk appeared to be corrupt or empty)

I was figuring that the synchronization had not occurred yet, and that there was still a good copy of the VMDK file on the '/dev/sdb2' partitoon, which appeared to still be a part of the '/dev/md1' array.  Attempts to remove '/dev/sdb2' from the array have not been successful.  I have used 'mdadm' to stop the array but meet with errors telling me the device is busy so it won;t remove the drive.

When I attempt to mount '/dev/md1' it cannot find a superblock.

When I run 'mdadm --examine /dev/md1' I get: "mdadm: No md superblock detected".  if I run the same command on '/dev/sdb2' (the member drive), I get:

```
/dev/sdb2:
          Magic : a92b4efc
        Version : 00.90.01
           UUID : a3e74676:d51643fa:22a2d47c:8443438a
  Creation Time : Tue Mar 11 21:53:16 2008
     Raid Level : raid1
    Device Size : 268558528 (256.12 GiB 275.00 GB)
     Array Size : 268558528 (256.12 GiB 275.00 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 1

    Update Time : Sun Mar 16 18:31:53 2008
          State : clean
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 68c5febd - correct
         Events : 0.10


      Number   Major   Minor   RaidDevice State
this     1       8       18        1      active sync   /dev/sdb2

   0     0       0        0        0      removed
   1     1       8       18        1      active sync   /dev/sdb2

```

There is a detectable XFS filesystem on the partition, which is good.  When I attempt to run 'xfs_repair -n /dev/md1' (which will only report what it would have done), it cannot find any primary superblock nor any suitable secondary superblocks.

I am almost certain that if I remove the '/dev/sdb2' from the md1 array, that I should then be able to mount it normally and hopefully recover the VMDK file, but I seemt o be able to remove it.

Any advice or tips greatly appreciated.

-SilkBC

---

