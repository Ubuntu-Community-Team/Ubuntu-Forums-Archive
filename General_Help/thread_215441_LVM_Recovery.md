---
title: "LVM Recovery"
date: 2006-07-13
forum: General Help
---

### Post by patsissons on 2006-07-13
I am completely stumped.  I am trying to recover someone's ubuntu install, which is (very unfortunately) using LVM.  I have tried just about every possible combination of commands to mount this LVM partition, however, no success in sight.  Here is the (typical) set of commands I have used and their respective responses.
```

root@cerberus:/tmp# vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "Ubuntu" using metadata type lvm2
root@cerberus:/tmp# vgchange -ay
  2 logical volume(s) in volume group "Ubuntu" now active
root@cerberus:/tmp# lvdisplay
  --- Logical volume ---
  LV Name                /dev/Ubuntu/root
  VG Name                Ubuntu
  LV UUID                IJ1tPo-jB85-d4GR-AW7k-V5C2-M1cD-3KwmA1
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                18.09 GB
  Current LE             4632
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           253:0

  --- Logical volume ---
  LV Name                /dev/Ubuntu/swap_1
  VG Name                Ubuntu
  LV UUID                h47vfK-sqOV-36vQ-9e1W-4yM1-WQ7v-YkLOlA
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                820.00 MB
  Current LE             205
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           253:1

root@cerberus:/tmp# mount /dev/Ubuntu/root /mnt
mount: you must specify the filesystem type

```

the purpose of the drives in question are fairly obvious, and I'm very certain that the commands I have used are not incorrect.  My question is why can I not mount the root partition?  Furthermore, I can't even mount the boot partition.  when I try to do that I get the following:

```

root@cerberus:/tmp# mount /dev/hde1 /mnt/
mount: wrong fs type, bad option, bad superblock on /dev/hde1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail

root@cerberus:/tmp# fdisk -l /dev/hde

Disk /dev/hde: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1          31      248976   83  Linux
/dev/hde2              32        2498    19816177+   5  Extended
/dev/hde5              32        2498    19816146   8e  Linux LVM

```

Anyone have any ideas on what to do to either get the drive to boot properly or to recover the LVM partition?  Currently, booting from hde will result in a fail when trying to mount the LVM partition, something about a missing mapper module which then falls back to a very basic ash shell.  Please Help!?!?

---

