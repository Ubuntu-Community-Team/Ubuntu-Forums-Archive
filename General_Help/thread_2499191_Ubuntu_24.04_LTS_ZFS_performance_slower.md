---
title: "Ubuntu 24.04 LTS ZFS performance slower"
date: 2024-07-18
forum: General Help
---

### Post by beloncfy on 2024-07-18
Hi
The ZFS on my new server with Ubuntu 24.04 is running slower than AlmaLinux, I have done the benchmark on the same server and the exact same zpool, below is the table of performance result.
[TABLE="width: 0"]
[TR]
[TD][/TD]
[TD]Ubuntu 24.04 LTS[/TD]
[TD]AlmaLinux 9.4[/TD]
[/TR]
[TR]
[TD]ZFS Send and Receive snapshot[/TD]
[TD]94 sec[/TD]
[TD]40 sec[/TD]
[/TR]
[TR]
[TD]FIO 4K random write[/TD]
[TD]IOPS=93.7k, BW=366MiB/s[/TD]
[TD]IOPS=182k, BW=712MiB/s[/TD]
[/TR]
[TR]
[TD]FIO 4K random read (Without Read Cache)[/TD]
[TD]IOPS=168k, BW=657MiB/s[/TD]
[TD]IOPS=205k, BW=802MiB/s[/TD]
[/TR]
[TR]
[TD]FIO 4K random read (With Read Cache)[/TD]
[TD]IOPS=467k, BW=1823MiB/s[/TD]
[TD]IOPS=576k, BW=2249MiB/s

[/TD]
[/TR]
[TR]
[TD]FIO 1M random write[/TD]
[TD]IOPS=1343, BW=1343MiB/s[/TD]
[TD]IOPS=2874, BW=2874MiB/s

[/TD]
[/TR]
[TR]
[TD]FIO 1M random read (Without Read Cache)[/TD]
[TD]IOPS=2098, BW=2099MiB/s[/TD]
[TD]IOPS=2731, BW=2732MiB/s

[/TD]
[/TR]
[TR]
[TD]FIO 1M random read (With Read Cache)[/TD]
[TD]IOPS=8752, BW=8752MiB/s[/TD]
[TD]IOPS=11.9k, BW=11.6GiB/s[/TD]
[/TR]
[/TABLE]

Possible that the Ubuntu ZFS is not really running in the kernel and lead to the performance issue?

---

