---
title: "mdadm mirror rebuild fails"
date: 2005-06-21
forum: General Help
---

### Post by qd989 on 2005-06-21
I've lost one of my drives in the mirror /dev/md0 

I am able to add the disk back in and resynch but when i reboot, the new drive falls off.

Is there something in grub that manages this? everything looks good before init 6

After adding the device:
```
root@lunar:/proc # cat /proc/mdstat 
Personalities : [raid1] 
md0 : active raid1 hdc2[0] hda2[1]
      77152064 blocks [2/2] [UU]
      
unused devices: <none>
```

How do the partitions look?

/dev/hda2
```
root@lunar:/proc # mdadm -E /dev/hda2
/dev/hda2:
          Magic : a92b4efc
        Version : 00.90.01
           UUID : c1d8baf7:701e4f9f:5b66f7b3:02a40caa
  Creation Time : Sun Jun 19 13:46:54 2005
     Raid Level : raid1
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Tue Jun 21 12:05:58 2005
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : c3351542 - correct
         Events : 0.7248


      Number   Major   Minor   RaidDevice State
this     1       3        2        1      active sync   /dev/hda2

   0     0      22        2        0      active sync   /dev/hdc2
   1     1       3        2        1      active sync   /dev/hda2


```

/dev/hdc2
```
root@lunar:/proc # mdadm -E /dev/hdc2
/dev/hdc2:
          Magic : a92b4efc
        Version : 00.90.01
           UUID : c1d8baf7:701e4f9f:5b66f7b3:02a40caa
  Creation Time : Sun Jun 19 13:46:54 2005
     Raid Level : raid1
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Tue Jun 21 12:06:13 2005
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : c335156a - correct
         Events : 0.7252


      Number   Major   Minor   RaidDevice State
this     0      22        2        0      active sync   /dev/hdc2

   0     0      22        2        0      active sync   /dev/hdc2
   1     1       3        2        1      active sync   /dev/hda2

```

Scans OK
```
root@lunar:/proc #  mdadm --detail --scan /dev/md0
/dev/md0:
        Version : 00.90.01
  Creation Time : Sun Jun 19 13:46:54 2005
     Raid Level : raid1
     Array Size : 77152064 (73.58 GiB 79.00 GB)
    Device Size : 77152064 (73.58 GiB 79.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Jun 21 12:07:33 2005
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : c1d8baf7:701e4f9f:5b66f7b3:02a40caa
         Events : 0.7266

    Number   Major   Minor   RaidDevice State
       0      22        2        0      active sync   /dev/hdc2
       1       3        2        1      active sync   /dev/hda2


```

And mdadm.conf  matches the scan...
```
root@lunar:/proc #  mdadm --detail --scan 
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=c1d8baf7:701e4f9f:5b66f7b3:02a40caa
   devices=/dev/hdc2,/dev/hda2
   
       
root@lunar:/proc # cat /etc/mdadm/mdadm.conf 
DEVICE partitions
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=c1d8baf7:701e4f9f:5b66f7b3:02a40caa
   devices=/dev/hdc2,/dev/hda2
```

init 6... and i get this: one drive short!```

root@lunar:~ # cat /proc/mdstat 
Personalities : [raid1] 
md0 : active raid1 hda2[1]
      77152064 blocks [2/1] [_U]
      
unused devices: <none>
root@lunar:~ # mdadm --detail --scan /dev/md0
/dev/md0:
        Version : 00.90.01
  Creation Time : Sun Jun 19 13:46:54 2005
     Raid Level : raid1
     Array Size : 77152064 (73.58 GiB 79.00 GB)
    Device Size : 77152064 (73.58 GiB 79.00 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Jun 21 16:54:21 2005
          State : active, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : c1d8baf7:701e4f9f:5b66f7b3:02a40caa
         Events : 0.9323

    Number   Major   Minor   RaidDevice State
       0       0        0        -      removed
       1       3        2        1      active sync   /dev/hda2
```


But the missing partion still has its info...
```
root@lunar:~ # mdadm -v -E /dev/hdc2
/dev/hdc2:
          Magic : a92b4efc
        Version : 00.90.01
           UUID : c1d8baf7:701e4f9f:5b66f7b3:02a40caa
  Creation Time : Sun Jun 19 13:46:54 2005
     Raid Level : raid1
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Tue Jun 21 14:43:47 2005
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : c3354384 - correct
         Events : 0.8426


      Number   Major   Minor   RaidDevice State
this     0      22        2        0      active sync   /dev/hdc2

   0     0      22        2        0      active sync   /dev/hdc2
   1     1       3        2        1      active sync   /dev/hda2

```

Add it back in, and repeat to no avail!

---

### Post by qd989 on 2005-06-21
Here's what I do to add the partition back in:

```

root@lunar:~ # mdadm --zero-superblock /dev/hdc2
root@lunar:~ # mdadm --add /dev/md0 /dev/hdc2
mdadm: hot added /dev/hdc2
root@lunar:~ # mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.01
  Creation Time : Sun Jun 19 13:46:54 2005
     Raid Level : raid1
     Array Size : 77152064 (73.58 GiB 79.00 GB)
    Device Size : 77152064 (73.58 GiB 79.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Jun 21 18:18:05 2005
          State : clean, degraded, recovering
 Active Devices : 1
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 1

 Rebuild Status : 0% complete

           UUID : c1d8baf7:701e4f9f:5b66f7b3:02a40caa
         Events : 0.9647

    Number   Major   Minor   RaidDevice State
       0       0        0        -      removed
       1       3        2        1      active sync   /dev/hda2

       2      22        2        0      spare rebuilding   /dev/hdc2
root@lunar:~ # cat /proc/mdstat 
Personalities : [raid1] 
md0 : active raid1 hdc2[2] hda2[1]
      77152064 blocks [2/1] [_U]
      [>....................]  recovery =  0.9% (695808/77152064) finish=49.4min speed=25770K/sec
unused devices: <none>
```

When the sync completes, is there a secondary commit or something?

---

