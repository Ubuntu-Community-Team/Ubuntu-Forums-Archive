---
title: "[SOLVED] cfdisk doesn't create devices ?"
date: 2008-06-09
forum: General Help
---

### Post by dbyrne on 2008-06-09
I've used cfdisk to partition a drive as below:

```
                          cfdisk (util-linux-ng 2.13)

                              Disk Drive: /dev/sdd
                       Size: 750156374016 bytes, 750.1 GB
             Heads: 255   Sectors per Track: 63   Cylinders: 91201

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    sdd1                    Primary   Linux raid autodetect            10001.95
    sdd5                    Logical   Linux raid autodetect             2994.01
    sdd6                    Logical   Linux raid autodetect           300000.64
    sdd7                    Logical   Linux raid autodetect           300000.64
                            Pri/Log   Free Space                      137156.55







     [Bootable]  [ Delete ]  [  Help  ]  [Maximize]  [ Print  ]
     [  Quit  ]  [  Type  ]  [ Units  ]  [ Write  ]

                 Toggle bootable flag of the current partition

```

Having written the partition table to the disk, I don't have a /dev/sdd7 device file, although the others (/dev/sdd1, sdd2, sdd5 and sdd6) all exist.

Any reason why sdd7 wouldn't be created ? How can I create it manually - I guess mknod, but how to find the device numbers ?

edit: I mknod'd a file, and also did one for sdc7:

```
# ls -l /dev/sdd*
brw-rw---- 1 root disk 8, 48 2008-06-09 22:38 /dev/sdd
brw-rw---- 1 root disk 8, 49 2008-06-09 22:07 /dev/sdd1
brw-rw---- 1 root disk 8, 50 2008-06-09 21:56 /dev/sdd2
brw-rw---- 1 root disk 8, 53 2008-06-09 22:17 /dev/sdd5
brw-rw---- 1 root disk 8, 54 2008-06-09 22:40 /dev/sdd6
# mknod /dev/sdd7 b 8 55
# chmod 660 /dev/sdd7
# ls -l /dev/sdd*
brw-rw---- 1 root disk 8, 48 2008-06-09 22:38 /dev/sdd
brw-rw---- 1 root disk 8, 49 2008-06-09 22:07 /dev/sdd1
brw-rw---- 1 root disk 8, 50 2008-06-09 21:56 /dev/sdd2
brw-rw---- 1 root disk 8, 53 2008-06-09 22:17 /dev/sdd5
brw-rw---- 1 root disk 8, 54 2008-06-09 22:40 /dev/sdd6
brw-rw---- 1 root root 8, 55 2008-06-09 22:55 /dev/sdd7

```

However there's still something wrong, as when I try to assemble these into a RAID array, the system complains:

```
# mdadm --create /dev/md3 --level=1 --raid-devices=2 /dev/sdc7 /dev/sdd7
mdadm: Cannot open /dev/sdc7: No such device or address
mdadm: Cannot open /dev/sdd7: No such device or address
mdadm: create aborted

```

Is there some limitation on the number of logical partitions or something that I'm not aware of ?

---

### Post by dbyrne on 2008-06-10
Fixed: rebooted, and all partitions came up.

I assume there's some kind of probe that runs at boot that solved this, and that I could probably have done it manually if I knew what to run, but it's fixed anyway.

---

