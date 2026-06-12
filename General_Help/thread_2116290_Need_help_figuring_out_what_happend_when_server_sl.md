---
title: "Need help figuring out what happend when server slowed to a crawl"
date: 2013-02-15
forum: General Help
---

### Post by nateswitch on 2013-02-15
I'm running an Ubuntu 10.04.4 LTS server.

Early this morning I started getting alerts stating the server was becoming unresponsive.  I was able to SSH in, see that apache2 was using all of the memory/virtual memory on the machine, killed apache2, and everything was fine again.

It took me about an hour to successfully SSH in and run the killall command

I'm seeing a lot of the following in my kern.log file, but I'm not sure what to make of them:
Feb 15 08:49:09 rse01 kernel: [739922.483200] apache2 invoked oom-killer: gfp_mask=0x280da, order=0, oom_adj=0
Feb 15 08:49:09 rse01 kernel: [739922.483207] apache2 cpuset=/ mems_allowed=0
Feb 15 08:49:09 rse01 kernel: [739922.483213] Pid: 3852, comm: apache2 Tainted: G        W  2.6.32-45-generic-pae #102-Ubuntu
Feb 15 08:49:09 rse01 kernel: [739922.483217] Call Trace:
Feb 15 08:49:09 rse01 kernel: [739922.483229]  [<c01d74a4>] oom_kill_process+0xa4/0x2b0
Feb 15 08:49:09 rse01 kernel: [739922.483235]  [<c01d7b19>] ? select_bad_process+0xa9/0xe0
Feb 15 08:49:09 rse01 kernel: [739922.483240]  [<c01d7ba1>] __out_of_memory+0x51/0xa0
Feb 15 08:49:09 rse01 kernel: [739922.483245]  [<c01d7c48>] out_of_memory+0x58/0xb0
Feb 15 08:49:09 rse01 kernel: [739922.483251]  [<c01da568>] __alloc_pages_slowpath+0x498/0x4b0
Feb 15 08:49:09 rse01 kernel: [739922.483257]  [<c01da6ba>] __alloc_pages_nodemask+0x13a/0x170
Feb 15 08:49:09 rse01 kernel: [739922.483264]  [<c01ed9ef>] do_anonymous_page+0x19f/0x3a0
Feb 15 08:49:09 rse01 kernel: [739922.483269]  [<c01f2137>] handle_mm_fault+0x417/0x4a0
Feb 15 08:49:09 rse01 kernel: [739922.483277]  [<c05bb36d>] do_page_fault+0x10d/0x3a0
Feb 15 08:49:09 rse01 kernel: [739922.483283]  [<c05bb260>] ? do_page_fault+0x0/0x3a0
Feb 15 08:49:09 rse01 kernel: [739922.483288]  [<c05b9223>] error_code+0x73/0x80
Feb 15 08:49:09 rse01 kernel: [739922.483303] Mem-Info:
Feb 15 08:49:09 rse01 kernel: [739922.483306] DMA per-cpu:
Feb 15 08:49:09 rse01 kernel: [739922.483310] CPU    0: hi:    0, btch:   1 usd:   0
Feb 15 08:49:09 rse01 kernel: [739922.483314] CPU    1: hi:    0, btch:   1 usd:   0
Feb 15 08:49:09 rse01 kernel: [739922.483318] CPU    2: hi:    0, btch:   1 usd:   0
Feb 15 08:49:09 rse01 kernel: [739922.483322] CPU    3: hi:    0, btch:   1 usd:   0
Feb 15 08:49:09 rse01 kernel: [739922.483325] Normal per-cpu:
Feb 15 08:49:09 rse01 kernel: [739922.483329] CPU    0: hi:  186, btch:  31 usd:   0
Feb 15 08:49:09 rse01 kernel: [739922.483333] CPU    1: hi:  186, btch:  31 usd:   0
Feb 15 08:49:09 rse01 kernel: [739922.483336] CPU    2: hi:  186, btch:  31 usd:   0
Feb 15 08:49:09 rse01 kernel: [739922.483340] CPU    3: hi:  186, btch:  31 usd:   1
Feb 15 08:49:09 rse01 kernel: [739922.483343] HighMem per-cpu:
Feb 15 08:49:09 rse01 kernel: [739922.483347] CPU    0: hi:  186, btch:  31 usd:  14
Feb 15 08:49:09 rse01 kernel: [739922.483351] CPU    1: hi:  186, btch:  31 usd:   0
Feb 15 08:49:09 rse01 kernel: [739922.483354] CPU    2: hi:  186, btch:  31 usd:   0
Feb 15 08:49:09 rse01 kernel: [739922.483358] CPU    3: hi:  186, btch:  31 usd:  16
Feb 15 08:49:09 rse01 kernel: [739922.483365] active_anon:1667851 inactive_anon:290004 isolated_anon:288
Feb 15 08:49:09 rse01 kernel: [739922.483367]  active_file:56 inactive_file:154 isolated_file:0
Feb 15 08:49:09 rse01 kernel: [739922.483369]  unevictable:0 dirty:0 writeback:207 unstable:0
Feb 15 08:49:09 rse01 kernel: [739922.483370]  free:60477 slab_reclaimable:6379 slab_unreclaimable:2271
Feb 15 08:49:09 rse01 kernel: [739922.483372]  mapped:0 shmem:39 pagetables:12333 bounce:0
Feb 15 08:49:09 rse01 kernel: [739922.483382] DMA free:8076kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15812kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:8kB slab_unreclaimable:16kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
Feb 15 08:49:09 rse01 kernel: [739922.483391] lowmem_reserve[]: 0 867 8034 8034
Feb 15 08:49:09 rse01 kernel: [739922.483409] Normal free:233108kB min:3732kB low:4664kB high:5596kB active_anon:243652kB inactive_anon:241672kB active_file:52kB inactive_file:268kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:887976kB mlocked:0kB dirty:0kB writeback:292kB mapped:12kB shmem:0kB slab_reclaimable:25508kB slab_unreclaimable:9068kB kernel_stack:2576kB pagetables:3548kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:690 all_unreclaimable? no
Feb 15 08:49:09 rse01 kernel: [739922.483418] lowmem_reserve[]: 0 0 57342 57342
Feb 15 08:49:09 rse01 kernel: [739922.483435] HighMem free:724kB min:512kB low:8224kB high:15940kB active_anon:6427752kB inactive_anon:918344kB active_file:172kB inactive_file:348kB unevictable:0kB isolated(anon):1152kB isolated(file):0kB present:7339792kB mlocked:0kB dirty:0kB writeback:536kB mapped:0kB shmem:156kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:45784kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:512 all_unreclaimable? no
Feb 15 08:49:09 rse01 kernel: [739922.483444] lowmem_reserve[]: 0 0 0 0
Feb 15 08:49:09 rse01 kernel: [739922.483455] DMA: 3*4kB 2*8kB 7*16kB 2*32kB 5*64kB 3*128kB 2*256kB 3*512kB 1*1024kB 2*2048kB 0*4096kB = 8076kB
Feb 15 08:49:09 rse01 kernel: [739922.483481] Normal: 142*4kB 16*8kB 584*16kB 465*32kB 354*64kB 228*128kB 153*256kB 93*512kB 30*1024kB 13*2048kB 3*4096kB = 233176kB
Feb 15 08:49:09 rse01 kernel: [739922.483505] HighMem: 29*4kB 11*8kB 18*16kB 4*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 620kB
Feb 15 08:49:09 rse01 kernel: [739922.483530] 100842 total pagecache pages
Feb 15 08:49:09 rse01 kernel: [739922.483533] 100676 pages in swap cache
Feb 15 08:49:09 rse01 kernel: [739922.483537] Swap cache stats: add 3205946, delete 3105270, find 43042/69457
Feb 15 08:49:09 rse01 kernel: [739922.483541] Free swap  = 0kB
Feb 15 08:49:09 rse01 kernel: [739922.483543] Total swap = 8388600kB
Feb 15 08:49:09 rse01 kernel: [739922.511038] 2228224 pages RAM
Feb 15 08:49:09 rse01 kernel: [739922.511043] 2000386 pages HighMem
Feb 15 08:49:09 rse01 kernel: [739922.511046] 180504 pages reserved
Feb 15 08:49:09 rse01 kernel: [739922.511049] 7885 pages shared
Feb 15 08:49:09 rse01 kernel: [739922.511052] 1986157 pages non-shared
Feb 15 08:49:09 rse01 kernel: [739922.511058] Out of memory: kill process 21754 (apache2) score 699064 or a child
Feb 15 08:49:09 rse01 kernel: [739922.511443] Killed process 21754 (apache2)

I'm hoping someone here can help shed some light on what caused apache2 to use all of the available memory on my computer so I can hopefully keep it from happening again.

Thanks!

---

### Post by TheFu on 2013-02-15
Is the system fully patched?
After the reboot, did apache use all RAM again and have the same issue?

Seems like having 8G of swap for a machine with 2G of real RAM is excessive.
What do your server performance graphs show? 
What is the normal amount of RAM used for the last week, month, year?

If you don't have monitoring, check out SysUsage or Cacti.  Having this data will help you know what the real issue is, not guess.

---

### Post by nateswitch on 2013-02-15
> **TheFu said:**
> Is the system fully patched?
Fully patched as of Feb 5.  Currently only shows a single update available: linux-image-2.6.32-45-generic-pae

> **TheFu said:**
> After the reboot, did apache use all RAM again and have the same issue?
No, after reboot it's acting normally

> **TheFu said:**
> Seems like having 8G of swap for a machine with 2G of real RAM is excessive.
There's actually 8GB of physical RAM, top confirms this.

> **TheFu said:**
> What do your server performance graphs show? 
What is the normal amount of RAM used for the last week, month, year?
For the last week/month/year, average physical RAM usage is 1GB, generally between .75-1.25GB used.

For swap, for the past week, no usage at all, last month, usually at 0GB, but sometimes goes as high as .1GB, last year, also generally at 0GB with it sometimes going up to about .1GB

CPU usage is almost nonexistent.

Unfortunately, my monitoring server died at 4:20 this morning, so I don't actually have any statistics for when the server actually froze up, but when I looked at top, memory, swap and CPU were at 100% load.

---

### Post by TheFu on 2013-02-15
Very nice to see someone running servers well.

Sounds like either a bug in the software stack or an attack.  Crashing a server is a common attack method as they search for ways to get their code to run in a corrupted process.

Hopefully you are better at getting logs off the machine immediately than I am.  Any funny access attempts to the machine or in the apache logs that might lead you to a subnet that needs to be blocked?

Would fail2ban be helpful?

If it cannot be reproduced, then I'd verify that no new "software" is on the box that you didn't place there, keep doing versioned backups, and be prepared to restore if/when something terrible happens.

Sorry that I'm no real help. Sounds like you are already doing everything you can.

---

