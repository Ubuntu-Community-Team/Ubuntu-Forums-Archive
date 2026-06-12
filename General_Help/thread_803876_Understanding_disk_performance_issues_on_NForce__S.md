---
title: "Understanding disk performance issues on NForce / SATA with iostat"
date: 2008-05-22
forum: General Help
---

### Post by mdmbkr on 2008-05-22
Greetings,

I am running some long computational processes (using GNU R) in parallel on an AMD64 multi-core system.  Each of the three processes needs access to an approximately 10GB fileset on disk to generate a result.  To avoid a disk bottleneck, I divided the input data among three physical drives, so each process reads data from only one of the drives.

The three disks used are of the following types:

WD740GD-00FL (raptor)
WD3000JD-00K
WD2500JD-00G

When monitoring the progress using 'top', I noticed that each process was generating a large number of major page faults (looking at the "nFLT" column, enabled by running top, then hitting 'f', then 'u', then enter). I also see that the kswapd processes have accumulated a lot of runtime. My initial reaction was that there was insufficient memory available, but this was not the case:

```

             total       used       free     shared    buffers     cached
Mem:       8179360    8139508      39852          0      11036    5464856
-/+ buffers/cache:    2663616    5515744
Swap:      8388592     633896    7754696

```

Do the page faults also include read requests that are not cached?

Furthermore, one of the processes has generated many more page faults than the others: 47 million, versus about 1.8 million.  So I ran iostat to try to get a better idea of what was really happening.  Here's a typical result:

```

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          45.91    0.00    3.96    3.70    0.00   46.43

Device:    rrqm/s wrqm/s   r/s   w/s  rsec/s  wsec/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await  svctm  %util
sda          4.33   0.37 119.36  0.37 29668.11    5.86 14834.06     2.93   247.85     0.60    4.99   4.94  59.17
sdc          1.63   0.52 1405.91  0.48 18740.02    8.00  9370.01     4.00    13.33     3.31    2.35   0.69  96.74

```

Why is the reads/sec (r/s) and average request size (avgrq-sz) so much smaller for sdc as compared to sda?  Notice how different the utilization is, too.  These two drives should have very similar performance characteristics.

The files being read have extension CEL.  Here's what I see from 'lsof':

```

# lsof | grep CEL
R         15073   auser    3r      REG                8,1  176098203    1622502 (a file on sda).CEL
R         16164   auser  mem       REG               8,33   69107203   12453619 (a file on sdc).CEL
R         16164   auser    3r      REG               8,33   69107203   12453619 (a files on sdc).CEL

```

Why is the file on sdc listed twice (with one entry memory mapped) but the same is not happening on sda?

Any insight would be most helpful :)

---

