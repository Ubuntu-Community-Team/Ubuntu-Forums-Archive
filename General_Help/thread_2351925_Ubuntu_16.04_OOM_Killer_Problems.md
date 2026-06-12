---
title: "Ubuntu 16.04 OOM Killer Problems"
date: 2017-02-07
forum: General Help
---

### Post by jay214128 on 2017-02-07
I am having problems with the kernel oom killer killing applications on Ubuntu 16.04 LTS.  Previously I was using Ubuntu 14.04 LTS and had no issues.  The system HD died, so when I replaced it, I also installed 16.04.  Now my same applications are getting killed by the oom killer.

The machine has 16GB of RAM and 8GB of swap space.  The main application of this machine is running rsync.  It is the same version of rsync (3.1.1) on both 14.04 and 16.04.  I see the following from dmesg

```
[317850.166034] Node 0 hugepages_total=0 hugepages_free=0 hugepages_surp=0 hugepages_size=1048576kB
[317850.166035] Node 0 hugepages_total=0 hugepages_free=0 hugepages_surp=0 hugepages_size=2048kB
[317850.166036] 1291818 total pagecache pages
[317850.166036] 5084 pages in swap cache
[317850.166037] Swap cache stats: add 2019507, delete 2014423, find 339031/521445
[317850.166038] Free swap  = 6078644kB
[317850.166038] Total swap = 8042492kB
[317850.166039] 2011021 pages RAM
[317850.166039] 0 pages HighMem/MovableOnly
[317850.166040] 52247 pages reserved
[317850.166040] 0 pages cma reserved
[317850.166041] 0 pages hwpoisoned

[317850.166187] [29106]     0 29106   176351    53136     351       3   100218             0 rsync
[317850.166188] [29107]     0 29107   218274    61397     432       3   140157             0 rsync
[317850.166189] [29108]     0 29108   162038    44158     322       3    91708             0 rsync
[317850.166190] Out of memory: Kill process 29107 (rsync) score 49 or sacrifice child
[317850.166195] Killed process 29108 (rsync) total-vm:648152kB, anon-rss:174952kB, file-rss:1680kB
[343191.873402] Purging GPU memory, 52301824 bytes freed, 5025792 bytes still pinned.
[381870.304410] Purging GPU memory, 53043200 bytes freed, 5025792 bytes still pinned.
[381870.305240] Purging GPU memory, 5058560 bytes freed, 5025792 bytes still pinned.
```

This says there was 6GB of free swap space available and the killed process was using only 648MB of VM.  Why is the oom killer now killing applications on 16.04 when it did not on 14.04?

---

### Post by guimli-sfx on 2017-02-08
Same problem.
Bug reported here : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1655842](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1655842)

I will try the kernel 4.4.0-63

No oom-killer that night with kernel 4.4.0.63

---

### Post by jay214128 on 2017-02-10
> **guimli-sfx said:**
> Same problem.
Bug reported here : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1655842](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1655842)

I will try the kernel 4.4.0-63

No oom-killer that night with kernel 4.4.0.63

Where did you get kernel 4.4.0-63?  I have 4.4.0-62 and it exhibits the problem.  There are no updates available for the kernel.

---

### Post by mc4man on 2017-02-11
> **jay214128 said:**
> Where did you get kernel 4.4.0-63?  I have 4.4.0-62 and it exhibits the problem.  There are no updates available for the kernel.
You'd find it in the -proposed repo
(- I wouldn't suggest doing a 'blanket' upgrade with -proposed enabled, may be better to enable, upgrade the kernel, then disable.

---

### Post by jay214128 on 2017-02-24
I have upgraded the kernel to 4.4.0-64.  I will keep an eye on it.

---

