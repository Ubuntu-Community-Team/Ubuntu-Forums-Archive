---
title: "OOM killer activation with tons of free RAM"
date: 2021-01-12
forum: General Help
---

### Post by jwbrase on 2021-01-12
My home desktop is running Ubuntu 20.04 and has 32 GB of RAM. Furthermore, I have an LVM volume group that provides storage for VMs, as well as a few directories I've split of into separate filesystems. The space on this volume group that is not assigned to any particular use is used as swap, and when I spin up a new VM, I shrink the swap space to make room for a new volume to be used as the disk for the VM. The current total amount of swap space on the system is around 750 GB (overkill, but the disk space isn't being used for anything else at the moment).

Typically, the total memory in use by programs is around 8 GB. I run a daily incremental backup that tends to churn a lot of data through the various filesystem metadata caches, but if the system needs more memory to fulfill program allocations, it should just be dropping that to free memory.

The problem is, I'm fairly frequently waking up to find programs that I had left open the previous night dead (often my browser, or steam), and when I check the logs, I'm finding that the OOM killer is the culprit. The machine is under a fairly typical desktop workload, plus VMs that use at most ~5 GB. I see no evidence that I'm at any time getting anywhere near 32 GB of allocations, and I can't imagine a memory spike that would fill the 750 GB of swap I have (not to mention that if such a spike did happen, most of the data in RAM before the spike would end up on swap afterward, and the system would crawl for a while when I came back to it, as everything was paged back in, but that isn't happening), but since the 8th, I have **3** separate occasions on which the OOM killer activated (on two of those occasions, the OOM killer activated twice within the space of a minute or so. The times in the logs seem to be consistently about an hour after my daily backup run. But it's an incremental backup, so the volume per day actually transferred is fairly low (generally not even 1 GB), and I can't imagine the memory usage of the backup process exceeding that. The backup does touch every file on the system, so the inode cache grows quite large (~10 GB currently), but once again, that's just a cache, so if the memory is actually needed for programs to use it should just be dropped.

Has anybody encountered this behavior before?

---

