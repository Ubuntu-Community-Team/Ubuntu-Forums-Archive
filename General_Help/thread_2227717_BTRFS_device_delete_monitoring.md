---
title: "BTRFS device delete monitoring?"
date: 2014-06-03
forum: General Help
---

### Post by bruce20 on 2014-06-03
There are probably better ways but this is what I noticed.

Originally had a 3TB and a 1TB while playing around and I filled up the 1TB by not paying attention. So I added a 4TB I had laying around and went to remove the 1TB using-

"btrfs device delete /dev/sdb /mnt" 

This seemed to be taking forever so I was curious as to what may actually be going on. I ran-

"btrfs fi show /dev/sdb"  

and got the following:

        Total devices 3 FS bytes used 1.81TiB
        devid    1 size 2.73TiB used 933.01GiB path /dev/sdc
        devid    2 size 0.00 used 737.01GiB path /dev/sdb
        devid    3 size 3.64TiB used 196.00GiB path /dev/sdd

I waited a while and did it again and got 

        Total devices 3 FS bytes used 1.81TiB
        devid    1 size 2.73TiB used 933.01GiB path /dev/sdc
        devid    2 size 0.00 used 699.01GiB path /dev/sdb
        devid    3 size 3.64TiB used 234.00GiB path /dev/sdd


So it looks like it is moving the data over from the 1TB to the 4TB. If any BTRFS Gurus can tell me if I am correct or wrong I would appreciate it.

**edit**
The moment it got down to 0 on /dev/sdb the device remove completed so I assume this works for monitoring.


B

---

