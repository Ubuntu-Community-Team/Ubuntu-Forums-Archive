---
title: "Software RAID 5 Crash!"
date: 2008-01-23
forum: General Help
---

### Post by Docfaux on 2008-01-23
I'm not sure what category this should go in, so I'll post here.

Server:
AMD Athlon XP 2000
512mb RAM
nVidia GeForce 6600 AGP
Software RAID 5
  3x Seagate 500gb (sda1, sdb1, sdc1)

Problem:
After setting up and transferring all of my data, I started editing on my new RAID setup through a SAMBA connection.  Eventually the network drive became sluggish to respond to my editing station, and then my server shutdown.  I believed this was a heat issue, as I didn't have enough fans in my box.  A stupid oversight.  I waited until the next day after I could get some fans to power my system on.  When I powered on the RAID array was no longer functioning.  Going into terminal and trying to manually assemble my array creates this:

```
mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1
mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.
```

So I try assembling to md1, just to see what happens, and it returns the same error.  Here are the mdadm -E for all of my drives.

```
/dev/sda1:
          Magic : a92b4efc
        Version : 01
    Feature Map : 0x1
     Array UUID : 8aac1acb:3587a61e:d19e59cd:208368f7
           Name : 0
  Creation Time : Mon Jan  7 17:10:05 2008
     Raid Level : raid5
   Raid Devices : 3

  Used Dev Size : 976767728 (465.76 GiB 500.11 GB)
     Array Size : 1953534976 (931.52 GiB 1000.21 GB)
      Used Size : 976767488 (465.76 GiB 500.10 GB)
   Super Offset : 976767984 sectors
          State : clean
    Device UUID : 9b301150:eda59be1:1cc3de34:65db148a

Internal Bitmap : -234 sectors from superblock
    Update Time : Mon Jan 14 06:10:39 2008
       Checksum : 860a3748 - correct
         Events : 16

         Layout : left-symmetric
     Chunk Size : 128K

    Array Slot : 0 (0, 1, failed, 2)
   Array State : Uuu 1 failed

```
```

/dev/sdb1:
          Magic : a92b4efc
        Version : 01
    Feature Map : 0x1
     Array UUID : 8aac1acb:3587a61e:d19e59cd:208368f7
           Name : 0
  Creation Time : Mon Jan  7 17:10:05 2008
     Raid Level : raid5
   Raid Devices : 3

  Used Dev Size : 976767728 (465.76 GiB 500.11 GB)
     Array Size : 1953534976 (931.52 GiB 1000.21 GB)
      Used Size : 976767488 (465.76 GiB 500.10 GB)
   Super Offset : 976767984 sectors
          State : clean
    Device UUID : b4257809:47c80640:d7dffc24:8220b1f8

Internal Bitmap : -234 sectors from superblock
    Update Time : Mon Jan 14 06:24:59 2008
       Checksum : fc93b402 - correct
         Events : 36

         Layout : left-symmetric
     Chunk Size : 128K

    Array Slot : 1 (failed, 1, failed, failed)
   Array State : _U_ 3 failed

```
```

/dev/sdc1:
          Magic : a92b4efc
        Version : 01
    Feature Map : 0x1
     Array UUID : 8aac1acb:3587a61e:d19e59cd:208368f7
           Name : 0
  Creation Time : Mon Jan  7 17:10:05 2008
     Raid Level : raid5
   Raid Devices : 3

  Used Dev Size : 976767728 (465.76 GiB 500.11 GB)
     Array Size : 1953534976 (931.52 GiB 1000.21 GB)
      Used Size : 976767488 (465.76 GiB 500.10 GB)
   Super Offset : 976767984 sectors
          State : clean
    Device UUID : 28c1f218:2e137f06:f670cbdf:95e9baee

Internal Bitmap : -234 sectors from superblock
    Update Time : Mon Jan 14 06:10:39 2008
       Checksum : 8361f123 - correct
         Events : 16

         Layout : left-symmetric
     Chunk Size : 128K

    Array Slot : 3 (0, 1, failed, 2)
   Array State : uuU 1 failed

```

Any ideas?

---

### Post by fjgaude on 2008-01-23
I can't say for sure what might be the problem. The heat could have killed one or two of the drives. One drive failure would cauds the array to be slow but still function.

You might try to fix the two bad drives by using this command, one at a time:

```
sudo e2fsck -C0 -p -f -v /dev/sd[n]1
```

for each of the drives you think are bad.

Let us know how you make out.

---

### Post by Docfaux on 2008-01-23
Thank you so much for the reply!  When I run e2fsck I get
```
e2fsck: Device or resource busy while trying to open /dev/sdc1
Filesystem mounted or opened exclusively by another program?
```
I already stopped the array.  Is there a way to force unmount or something similar?

Also, I'm not sure if any of the drives could have died.  I wasn't running them hot for too long, and they were brand new.  They're still under warranty, so I'm not worried about losing cash, just data.  So here's hoping they still work!

---

### Post by fjgaude on 2008-01-25
Try another command:

```
sudo mdadm --assemble --scan --verbose
```

and see what you get.

---

