---
title: "Is the output for iostat reversed?"
date: 2012-11-30
forum: General Help
---

### Post by gc55555 on 2012-11-30
The following is from my home desktop computer running 12.04 with three disks (sda is a SSD with the OS and LVM, sdb and sdc are regular SATA drives with plain partitions set up as a RAID1 for data and home).

When I look at the output for iostat, the writes are a lot higher than the reads! That just doesn't sound right. Here is the output for iostat.

[FONT=Courier New][SIZE=1]gmc@gmc:~/rrd$ iostat
Linux 3.2.0-32-generic (gmc)     11/30/2012     _x86_64_    (4 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           1.42    0.01    1.24    0.16    0.00   97.18

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sda               1.77         6.56        47.33    1108673    8001504
sdb               2.13         6.20        41.05    1047600    6940212
sdc               2.10         6.05        41.05    1023423    6940212
md0               3.19        12.24        40.85    2069179    6905868
dm-0              1.78         0.80        19.71     134845    3331784
dm-1              1.20        11.39        21.14    1925209    3574036
dm-2              0.01         0.05         0.00       8993         48
sdd               0.01         0.03         0.00       4749          2[/SIZE][/FONT]

---

