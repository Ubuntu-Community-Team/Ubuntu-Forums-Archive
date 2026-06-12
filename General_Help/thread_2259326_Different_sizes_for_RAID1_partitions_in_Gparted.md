---
title: "Different sizes for RAID1 partitions in Gparted"
date: 2015-01-03
forum: General Help
---

### Post by jones.79 on 2015-01-03
Hello,


I came across a strage thing and hope that you can help me.

With one of three RAID1 arrays (Boot, System, Home) the size of the ext4 partitions shown in Gparted is not identical.

The size of Boot and System is identical but Home is deviating at "Size" and "Used" while "Unused" is correct.

```
 (Size [GiB] / Used [GiB] / Unused [GiB])
sda7: 419.19 / 268.27 / 150.92
sdb7: 421.10 / 270.18 / 150.92 
```

```
 cat /proc/mdstat
Personalities : [raid1] 
md0 : active raid1 sda7[0] sdb7[1]
      439552960 blocks [2/2] [UU]
unused devices: <none>
```

Any ideas on this? Is this normal (RAID overhead?) or might there be a problem?

Edit:

I just found out that

```
 sudo mdmadm --examine /dev/sdxx
```

states that both RAID partitions have the same size and same usage.
I guess that is more reliable than Gparted...

Cheers,
Markus

---

