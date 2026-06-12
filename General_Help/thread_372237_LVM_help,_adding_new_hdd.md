---
title: "LVM help, adding new hdd"
date: 2007-02-27
forum: General Help
---

### Post by NJHokie on 2007-02-27
hey all,
i added a 3rd hdd to my system today and tried to extend the logical volume i currently had with the new added space.  it was previously a windows NTFS disk (formatted clean before transfer).  after going through the steps it all displays properly under "vgdisplay -v" but when i actually go and check the mount point folder size it is still the same as before and has not increased along w/ the volume group and logical volume.  

I've tried to remove the hdd from the VG to try and redo it but i get errors when trying to use "vgreduce" to remove the PV, saying "physical volume "dev/hdd1" still in use", even after running a "pvmove" command which resulted in "no extents avail for allocation".  

LV is being used by mythtv btw.
Any help resolving this would be greatly appreciated, Thanks!

here are the results of vgdisplay -v.  it should be as it says, 203GB but it shows up as 130GB still when i browse /home/nick/video (mount point)

nick@ubuntu:~$ sudo vgdisplay -v
    Finding all volume groups
    Finding volume group "VGforMyth"
  --- Volume group ---
  VG Name               VGforMyth
  System ID             
  Format                lvm2
  Metadata Areas        3
  Metadata Sequence No  5
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               0
  Max PV                0
  Cur PV                3
  Act PV                3
  VG Size               208.31 GB
  PE Size               64.00 MB
  Total PE              3333
  Alloc PE / Size       3333 / 208.31 GB
  Free  PE / Size       0 / 0   
  VG UUID               C8kSGQ-rAw1-GmUi-7oKx-zatX-8D1A-bYuK35
   
  --- Logical volume ---
  LV Name                /dev/VGforMyth/video
  VG Name                VGforMyth
  LV UUID                q6mYAL-6r5u-92bK-xeIc-qttc-Zmxk-00e0rS
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                208.31 GB
  Current LE             3333
  Segments               3
  Allocation             inherit
  Read ahead sectors     0
  Block device           253:0
   
  --- Physical volumes ---
  PV Name               /dev/hda4     
  PV UUID               9VmJ6M-UxhP-7LRF-SAOE-ix3l-pSWe-a2ueRL
  PV Status             allocatable
  Total PE / Free PE    950 / 0
   
  PV Name               /dev/hdb1     
  PV UUID               tCKbgt-nBvc-r8FS-OxEd-u9XW-NiOA-00q0BI
  PV Status             allocatable
  Total PE / Free PE    1192 / 0
   
  PV Name               /dev/hdd1     
  PV UUID               KEBtSE-LKcc-l79g-2NSh-6VLQ-HKoG-l0zciX
  PV Status             allocatable
  Total PE / Free PE    1191 / 0

---

### Post by NJHokie on 2007-02-28
here's some additional info on what i may have done wrong:

i first ran fdisk on /dev/hdd1, the partition, instead of the whole disk /dev/hdd.  i created a partition, sized it to take the full space, changed it to 8e, which gave me /dev/hdd1p1.  which i really didn't want, but it happened anyway.

i then did a pvcreate /dev/hdd1, not hdd1p1, then did "vgextend VGforMyth /dev/hdd1"  then did "lvextend --size +79.3G /dev/VGforMyth/video" 

somewhere along the way i realized what i was doing wrong and went back and fdisk'ed /dev/hdd to remove the two partitions and create a new correct partition /dev/hdd1 set to 8e and extending the entire disk.  now /dev/hdd1 was till part of the VG while "fixing" the issue.  i'm guessing i screwed it up somewhere along the way.  

is there a way to fix the LV as it is?  or should i wipe it all out and start over?  if so, how do i go about doing that?  do i delete all data on the LV then do a vgremove then fdisk everything, deleting all partitions and start over?

---

