---
title: "BTRFS Convert Raid5 to Raid1"
date: 2016-12-11
forum: General Help
---

### Post by joachim.nielandt on 2016-12-11
Hi all,

I'm in the process of acknowledging that my 4-disk NAS is running a potentially flawed RAID5 btrfs installation. So, I did the sensible thing: convert it to RAID1

```
btrfs balance start -dconvert=raid1 -mconvert=raid1 /pool
```

This took a while, and I'm left with some questions to which I don't seem to find an answer to. A quick printout of my btrfs volume:

```
~# btrfs fi usage /poolWARNING: RAID56 detected, not implemented
Overall:
    Device size:           9.10TiB
    Device allocated:           4.26TiB
    Device unallocated:           4.84TiB
    Device missing:             0.00B
    Used:               4.24TiB
    Free (estimated):           2.44TiB    (min: 2.43TiB)
    Data ratio:                  1.99
    Metadata ratio:              2.00
    Global reserve:         512.00MiB    (used: 0.00B)


Data,RAID1: Size:2.12TiB, Used:2.11TiB
   /dev/sda     625.00GiB
   /dev/sdb     625.00GiB
   /dev/sdc       1.51TiB
   /dev/sde       1.51TiB


Data,RAID5: Size:9.00GiB, Used:6.44GiB
   /dev/sda       3.00GiB
   /dev/sdb       3.00GiB
   /dev/sdc       3.00GiB
   /dev/sde       3.00GiB


Metadata,RAID1: Size:5.00GiB, Used:4.18GiB
   /dev/sdc       5.00GiB
   /dev/sde       5.00GiB


System,RAID1: Size:32.00MiB, Used:336.00KiB
   /dev/sda      32.00MiB
   /dev/sdb      32.00MiB


Unallocated:
   /dev/sda       1.21TiB
   /dev/sdb       1.21TiB
   /dev/sdc       1.21TiB
   /dev/sde       1.21TiB

```

It seems that the RAID5 data has not disappeared completely, although there is no more RAID5 metadata to be found. I'd love to completely see the RAID56 warning disappear, along with the RAID5 data. Additionally: it is not entirely clear to me in which way new data will be written to the array. Will it be RAID1? How can I verify the 'current setting' of the BTRFS volume?

Thanks in advance!
Joa

:mod: I redid the conversion, using the following command to only target raid5 chunks:
```
balance start -v -dprofiles=raid5 -mprofiles=raid5 -dconvert=raid1 -mconvert=raid1 /pool
```
Now the raid5 blocks have disappeared. Still odd that some would not be converted (the relevant files were in use, perhaps?). And some of my confusion remains: how can you see what' s the 'current setting'? Is it because there's blocks with System,RAID1 present?

---

