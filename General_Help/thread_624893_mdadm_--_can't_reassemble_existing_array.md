---
title: "mdadm -- can't reassemble existing array"
date: 2007-11-27
forum: General Help
---

### Post by abacabb on 2007-11-27
Hello, all!

I'm hoping you can help out - I'm a bit boggled as this is the second time this has happened....

I have a RAID0 array spanning one internal drive and a RAID5 USB device (sdb1 and sdc1... yeah yeah.. I know the evils of RAID0 - drive space is more important right now). About once a month, the USB RAID goes off-line and, obviously, takes the entire array with it. I don't seem to be able to get the array back on-line, however... it just refuses to see the USB device.

An example:
# cat /proc/mdstat
Personalities : 
md0 : inactive sdb1[0](S) sdc1[1](S)
      1367492736 blocks
       
unused devices: <none>

# mdadm --run /dev/md0
mdadm: failed to run array /dev/md0: Cannot allocate memory

In dmesg:
[ 3078.982707] raid0: looking at sdb1
[ 3078.982709] raid0:   comparing sdb1(390708736) with sdb1(390708736)
[ 3078.982712] raid0:   END
[ 3078.982713] raid0:   ==> UNIQUE
[ 3078.982715] raid0: 1 zones
[ 3078.982716] raid0: FINAL 1 zones
[ 3078.982718] raid0: too few disks (1 of 2) - aborting!
[ 3078.982720] md: pers->run() failed ...

# fdisk -l /dev/sdc
/dev/sdc1               1      121604   976784098+  fd  Linux raid autodetect

If I force the --run, it will complain, of course, and I don't want to do that for fear that it'll mess up the superblock. 

I'm coming from the NetBSD world, and I could most likely correct this with raidctl without issue. I'm not sure what mdadm is/isn't doing where it sees the partitions but can't at the same time.

While the data on the array isn't super critical, the fact that this happens once/month and my only recourse is to drop the data and recreate the array is bothersome, to say the least.  I'd rather just be able to fix the array and pick up where I left off. 

Any help is greatly appreciated!

---

### Post by fjgaude on 2007-11-27
I'm not sure I will be of any help, but here goes. What does sudo mdadm -D /dev/md0 show?

---

### Post by abacabb on 2007-11-27
Oops - thank you - I did forget to post the results of that. 

# mdadm -D /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Wed Oct 24 13:30:23 2007
     Raid Level : raid0
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Nov 27 11:05:29 2007
          State : active, degraded, Not Started
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : 52f07599:09e468c4:f330d9af:4f8fb28d (local to host ql1cma1.quickenloans.com)
         Events : 0.5

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       0        0        1      removed

dmesg does show:

[ 3020.447617] md: kicking non-fresh sdc1 from array!
[ 3020.447625] md: unbind<sdc1>
[ 3020.447633] md: export_rdev(sdc1)

I've  not seen part of an array go to non-fresh before and then not even be able to be added back in.

---

### Post by fjgaude on 2007-11-28
I tell you I have no answer for a raid0 array with two disks with one of them declared as "bad". You see if mdadm cannot assemble it can't add back. This seems to be the case here. Are your drives in good shape, relatively new?

I wouldn't recommend raid0 except with full data backup. I boot from a single fast drive and use soft link to data raid5. Has worked just fine over time.

---

### Post by abacabb on 2007-11-28
Yeah - I do know that the second "drive" (sdc1) is fine... it's a USB RAID5 device that I'm just concatenating to another internal drive (sdb1). Not an ideal solution, but it works for now. The RAID5 device doesn't report any errors and self-tests fine. When it drops out of the RAID, linux reports USB errors, as if it was just unplugged. The problem is that after subsequent reboots, the system will see the USB device, but can't reassemble the array with it. If I drop the existing RAID0 array and start over, everything is fine.

I'm not sure if this is a mdadm RAID0 issue that maybe hasn't been caught since it's not used that often, or what.

---

### Post by fjgaude on 2007-11-29
What is a USB RAID5 device?

---

