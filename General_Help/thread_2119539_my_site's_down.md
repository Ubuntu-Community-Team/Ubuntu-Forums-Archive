---
title: "my site's down"
date: 2013-02-24
forum: General Help
---

### Post by jaawis on 2013-02-24
Hello, i have since a few days some problem with my vps, my website's are getting down, only after a reboot they are back for a few minutes.
 
SSH is breaking the conection after a few minutes or seconds to..
So i have not much time to change things.
 
One thing i noticed i that my kern log, messages and syslog had grown all three to over the 400 mb in just one day.
 
Now i dont know what to do, hope somebody can help me.
After deleting my log files, they are not growing that fast anymore...
But my website's are still getting down all the time
 
Some output from the big logfiles that are reapted allot of times:
 
```

Feb 24 05:30:46 host kernel: [47481.451145] 262142 pages RAM
Feb 24 05:30:46 host kernel: [47481.451147] 5429 pages reserved
Feb 24 05:30:46 host kernel: [47481.451149] 17489 pages shared
Feb 24 05:30:46 host kernel: [47481.451151] 241334 pages non-shared
Feb 24 05:30:46 host kernel: [47481.451154] Out of memory: kill process 1269 (apache2) score 335419 or a child
Feb 24 05:30:46 host kernel: [47481.452061] Killed process 5281 (apache2)
Feb 24 05:30:46 host kernel: [47481.454322] php5-cgi invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0
Feb 24 05:30:46 host kernel: [47481.454341] php5-cgi cpuset=/ mems_allowed=0
Feb 24 05:30:46 host kernel: [47481.454344] Pid: 11627, comm: php5-cgi Not tainted 2.6.32-5-amd64 #1
Feb 24 05:30:46 host kernel: [47481.454346] Call Trace:
Feb 24 05:30:46 host kernel: [47481.454355] [<ffffffff810b643c>] ? oom_kill_process+0x7f/0x23f
Feb 24 05:30:46 host kernel: [47481.454360] [<ffffffff8106bb5e>] ? timekeeping_get_ns+0xe/0x2e
Feb 24 05:30:46 host kernel: [47481.454363] [<ffffffff810b6960>] ? __out_of_memory+0x12a/0x141
Feb 24 05:30:46 host kernel: [47481.454365] [<ffffffff810b6ab7>] ? out_of_memory+0x140/0x172
Feb 24 05:30:46 host kernel: [47481.454369] [<ffffffff810ba81c>] ? __alloc_pages_nodemask+0x4ec/0x5fc
Feb 24 05:30:46 host kernel: [47481.454374] [<ffffffff812fbb8a>] ? io_schedule+0x93/0xb7
Feb 24 05:30:46 host kernel: [47481.454378] [<ffffffff810bbd85>] ? __do_page_cache_readahead+0x9b/0x1b4
Feb 24 05:30:46 host kernel: [47481.454382] [<ffffffff81065074>] ? wake_bit_function+0x0/0x23
Feb 24 05:30:46 host kernel: [47481.454386] [<ffffffff810bbeba>] ? ra_submit+0x1c/0x20
Feb 24 05:30:46 host kernel: [47481.454389] [<ffffffff810b4b87>] ? filemap_fault+0x17d/0x2f6
Feb 24 05:30:46 host kernel: [47481.454394] [<ffffffff810cab26>] ? __do_fault+0x54/0x3c3
Feb 24 05:30:46 host kernel: [47481.454398] [<ffffffff812fbfb1>] ? __wait_on_bit_lock+0x76/0x84
Feb 24 05:30:46 host kernel: [47481.454401] [<ffffffff810cce7a>] ? handle_mm_fault+0x3b8/0x80f
Feb 24 05:30:46 host kernel: [47481.454407] [<ffffffff812ff306>] ? do_page_fault+0x2e0/0x2fc
Feb 24 05:30:47 host kernel: [47481.454411] [<ffffffff812fd1a5>] ? page_fault+0x25/0x30
Feb 24 05:30:47 host kernel: [47481.454413] Mem-Info:
Feb 24 05:30:47 host kernel: [47481.454415] Node 0 DMA per-cpu:
Feb 24 05:30:47 host kernel: [47481.454419] CPU 0: hi: 0, btch: 1 usd: 0
Feb 24 05:30:47 host kernel: [47481.454421] CPU 1: hi: 0, btch: 1 usd: 0
Feb 24 05:30:47 host kernel: [47481.454423] Node 0 DMA32 per-cpu:
Feb 24 05:30:47 host kernel: [47481.454455] CPU 0: hi: 186, btch: 31 usd: 30
Feb 24 05:30:47 host kernel: [47481.454457] CPU 1: hi: 186, btch: 31 usd: 0
Feb 24 05:30:47 host kernel: [47481.454462] active_anon:112765 inactive_anon:112867 isolated_anon:1367
Feb 24 05:30:47 host kernel: [47481.454464] active_file:61 inactive_file:126 isolated_file:42
Feb 24 05:30:47 host kernel: [47481.454465] unevictable:0 dirty:0 writeback:168 unstable:0
Feb 24 05:30:47 host kernel: [47481.454466] free:1992 slab_reclaimable:3666 slab_unreclaimable:4676
Feb 24 05:30:47 host kernel: [47481.454467] mapped:5672 shmem:66168 pagetables:13445 bounce:0
Feb 24 05:30:47 host kernel: [47481.454470] Node 0 DMA free:4028kB min:60kB low:72kB high:88kB active_anon:4268kB inactive_anon:4500kB active_file:8kB inactive_file:20kB unevictable:0kB isolated(anon):256kB isolated(file):0kB present:15372kB mlocked:0kB dirty:0kB writeback:8kB mapped:156kB shmem:1360kB slab_reclaimable:816kB slab_unreclaimable:640kB kernel_stack:536kB pagetables:472kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
Feb 24 05:30:47 host kernel: [47481.454481] lowmem_reserve[]: 0 994 994 994
Feb 24 05:30:47 host kernel: [47481.454485] Node 0 DMA32 free:3940kB min:4000kB low:5000kB high:6000kB active_anon:446792kB inactive_anon:446968kB active_file:236kB inactive_file:384kB unevictable:0kB isolated(anon):5212kB isolated(file):296kB present:1018072kB mlocked:0kB dirty:0kB writeback:664kB mapped:22532kB shmem:263312kB slab_reclaimable:13848kB slab_unreclaimable:18064kB kernel_stack:3072kB pagetables:53308kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:320 all_unreclaimable? no
Feb 24 05:30:47 host kernel: [47481.454496] lowmem_reserve[]: 0 0 0 0
Feb 24 05:30:47 host kernel: [47481.454500] Node 0 DMA: 703*4kB 0*8kB 24*16kB 16*32kB 5*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 4028kB
Feb 24 05:30:47 host kernel: [47481.454509] Node 0 DMA32: 779*4kB 7*8kB 2*16kB 3*32kB 0*64kB 1*128kB 0*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 3940kB
```

---

### Post by matt_symes on 2013-02-24
Hi

> om_kill_processIt looks like out of memory and processes including apache and php are getting killed. How much memory do you have in the VPS ?

You may have a runaway process or php script ?

What the output of

> cat /proc/sys/vm/panic_on_oom

You may be kernel panicing on an oom condition.

Kind regards

---

### Post by prodigy_ on 2013-02-24
> Feb 24 05:30:46 host kernel: [47481.451154] Out of memory: kill process 1269 (apache2) score 335419 or a child

Apache runs out of memory and gets killed. This could be caused by a broken PHP script.

[http://serverfault.com/questions/383291/apache-out-of-memory](http://serverfault.com/questions/383291/apache-out-of-memory)
[http://egloo.wordpress.com/2008/07/27/apache-out-of-memory-error/](http://egloo.wordpress.com/2008/07/27/apache-out-of-memory-error/)

---

### Post by jaawis on 2013-02-24
Im using fresh instalations of wordpress, with allot modifications, but there are no problems in the php.
 
the output from cat /proc/sys/vm/panic_on_oom, returns me 0.
 
I have 4500 mb memory

My messages log has this stuff in in, also i dont understand what this means:

```

Feb 21 21:19:05 host kernel: [474922.266998] php5-cgi cpuset=/ mems_allowed=0
Feb 21 21:19:05 host kernel: [474922.267005] Pid: 23091, comm: php5-cgi Not tainted 2.6.32-5-amd64 #1
Feb 21 21:19:05 host kernel: [474922.267008] Call Trace:
Feb 21 21:19:05 host kernel: [474922.267023] [<ffffffff810b643c>] ? oom_kill_process+0x7f/0x23f
Feb 21 21:19:05 host kernel: [474922.267031] [<ffffffff8106bb5e>] ? timekeeping_get_ns+0xe/0x2e
Feb 21 21:19:05 host kernel: [474922.267037] [<ffffffff810b6960>] ? __out_of_memory+0x12a/0x141
Feb 21 21:19:05 host kernel: [474922.267042] [<ffffffff810b6ab7>] ? out_of_memory+0x140/0x172
Feb 21 21:19:05 host kernel: [474922.267048] [<ffffffff810ba81c>] ? __alloc_pages_nodemask+0x4ec/0x5fc
Feb 21 21:19:05 host kernel: [474922.267056] [<ffffffff81111a75>] ? bio_alloc+0x10/0x1f
Feb 21 21:19:05 host kernel: [474922.267064] [<ffffffff810d8fd4>] ? read_swap_cache_async+0x5d/0xf3
Feb 21 21:19:05 host kernel: [474922.267070] [<ffffffff810d90c1>] ? swapin_readahead+0x57/0x98
Feb 21 21:19:05 host kernel: [474922.267075] [<ffffffff810ccf41>] ? handle_mm_fault+0x47f/0x80f
Feb 21 21:19:05 host kernel: [474922.267085] [<ffffffff812ff306>] ? do_page_fault+0x2e0/0x2fc
Feb 21 21:19:05 host kernel: [474922.267091] [<ffffffff812fd1a5>] ? page_fault+0x25/0x30
Feb 21 21:19:05 host kernel: [474922.267094] Mem-Info:
Feb 21 21:19:05 host kernel: [474922.267097] Node 0 DMA per-cpu:
Feb 21 21:19:05 host kernel: [474922.267102] CPU 0: hi: 0, btch: 1 usd: 0
Feb 21 21:19:05 host kernel: [474922.267105] CPU 1: hi: 0, btch: 1 usd: 0
Feb 21 21:19:05 host kernel: [474922.267159] Node 0 DMA32 per-cpu:
Feb 21 21:19:05 host kernel: [474922.267165] CPU 0: hi: 186, btch: 31 usd: 75
Feb 21 21:19:05 host kernel: [474922.267170] CPU 1: hi: 186, btch: 31 usd: 98
Feb 21 21:19:05 host kernel: [474922.267183] active_anon:115340 inactive_anon:115371 isolated_anon:1184
Feb 21 21:19:05 host kernel: [474922.267185] active_file:191 inactive_file:215 isolated_file:0
Feb 21 21:19:05 host kernel: [474922.267188] unevictable:0 dirty:2 writeback:177 unstable:0
Feb 21 21:19:05 host kernel: [474922.267190] free:1984 slab_reclaimable:3399 slab_unreclaimable:4102
Feb 21 21:19:05 host kernel: [474922.267193] mapped:15885 shmem:71935 pagetables:10130 bounce:0
Feb 21 21:19:05 host kernel: [474922.267198] Node 0 DMA free:4036kB min:60kB low:72kB high:88kB active_anon:5228kB inactive_anon:5436kB active_file:28kB inactive_file:16kB unevictable:0kB isolated(anon):128kB isolated(file):0kB present:15372kB mlocked:0kB dirty:0kB writeback:8kB mapped:760kB shmem:2968kB slab_reclaimable:364kB slab_unreclaimable:168kB kernel_stack:80kB pagetables:308kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:40 all_unreclaimable? no
Feb 21 21:19:05 host kernel: [474922.267222] lowmem_reserve[]: 0 994 994 994
Feb 21 21:19:05 host kernel: [474922.267231] Node 0 DMA32 free:3900kB min:4000kB low:5000kB high:6000kB active_anon:456132kB inactive_anon:456048kB active_file:736kB inactive_file:844kB unevictable:0kB isolated(anon):4608kB isolated(file):0kB present:1018072kB mlocked:0kB dirty:8kB writeback:700kB mapped:62780kB shmem:284772kB slab_reclaimable:13232kB slab_unreclaimable:16240kB kernel_stack:1656kB pagetables:40212kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:2646 all_unreclaimable? yes
Feb 21 21:19:05 host kernel: [474922.267294] lowmem_reserve[]: 0 0 0 0
Feb 21 21:19:05 host kernel: [474922.267300] Node 0 DMA: 122*4kB 177*8kB 21*16kB 6*32kB 3*64kB 3*128kB 2*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 4032kB
Feb 21 21:19:05 host kernel: [474922.267313] Node 0 DMA32: 285*4kB 143*8kB 43*16kB 5*32kB 2*64kB 1*128kB 0*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 3900kB
Feb 21 21:19:05 host kernel: [474922.267326] 100481 total pagecache pages
Feb 21 21:19:05 host kernel: [474922.267329] 28098 pages in swap cache
Feb 21 21:19:05 host kernel: [474922.267332] Swap cache stats: add 30094807, delete 30066709, find 7155682/10376300
Feb 21 21:19:05 host kernel: [474922.267335] Free swap = 0kB
Feb 21 21:19:05 host kernel: [474922.267337] Total swap = 2007032kB
Feb 21 21:19:05 host kernel: [474922.273113] 262142 pages RAM
Feb 21 21:19:05 host kernel: [474922.273117] 5429 pages reserved
Feb 21 21:19:05 host kernel: [474922.273119] 30971 pages shared
Feb 21 21:19:05 host kernel: [474922.273121] 230453 pages non-shared
Feb 21 21:20:14 host kernel: [474990.053395] php5-cgi invoked oom-killer: gfp_mask=0x200da, order=0, oom_adj=0
Feb 21 21:20:25 host kernel: [474990.053403] php5-cgi cpuset=/ mems_allowed=0
Feb 21 21:20:25 host kernel: [474990.053408] Pid: 23168, comm: php5-cgi Not tainted 2.6.32-5-amd64 #1
Feb 21 21:20:25 host kernel: [474990.053412] Call Trace:
Feb 21 21:20:25 host kernel: [474990.053424] [<ffffffff810b643c>] ? oom_kill_process+0x7f/0x23f
Feb 21 21:20:25 host kernel: [474990.053431] [<ffffffff8106bb5e>] ? timekeeping_get_ns+0xe/0x2e
Feb 21 21:20:25 host kernel: [474990.053436] [<ffffffff810b6960>] ? __out_of_memory+0x12a/0x141
Feb 21 21:20:25 host kernel: [474990.053440] [<ffffffff810b6ab7>] ? out_of_memory+0x140/0x172
Feb 21 21:20:25 host kernel: [474990.053446] [<ffffffff81041238>] ? pick_next_task_fair+0xca/0xd6
Feb 21 21:20:25 host kernel: [474990.053452] [<ffffffff810ba81c>] ? __alloc_pages_nodemask+0x4ec/0x5fc
Feb 21 21:20:25 host kernel: [474990.053459] [<ffffffff810d8fd4>] ? read_swap_cache_async+0x5d/0xf3
Feb 21 21:20:25 host kernel: [474990.053464] [<ffffffff810d90c1>] ? swapin_readahead+0x57/0x98
Feb 21 21:20:25 host kernel: [474990.053469] [<ffffffff810ccf41>] ? handle_mm_fault+0x47f/0x80f
Feb 21 21:20:25 host kernel: [474990.053477] [<ffffffff812ff306>] ? do_page_fault+0x2e0/0x2fc
Feb 21 21:20:25 host kernel: [474990.053483] [<ffffffff812fd1a5>] ? page_fault+0x25/0x30
Feb 21 21:20:25 host kernel: [474990.053486] Mem-Info:
Feb 21 21:20:25 host kernel: [474990.053488] Node 0 DMA per-cpu:
Feb 21 21:20:25 host kernel: [474990.053492] CPU 0: hi: 0, btch: 1 usd: 0
Feb 21 21:20:25 host kernel: [474990.053496] CPU 1: hi: 0, btch: 1 usd: 0
Feb 21 21:20:25 host kernel: [474990.053498] Node 0 DMA32 per-cpu:
Feb 21 21:20:25 host kernel: [474990.053502] CPU 0: hi: 186, btch: 31 usd: 19
Feb 21 21:20:25 host kernel: [474990.053505] CPU 1: hi: 186, btch: 31 usd: 85
Feb 21 21:20:25 host kernel: [474990.053513] active_anon:114957 inactive_anon:115025 isolated_anon:1568
Feb 21 21:20:25 host kernel: [474990.053514] active_file:478 inactive_file:292 isolated_file:0
Feb 21 21:20:25 host kernel: [474990.053516] unevictable:0 dirty:0 writeback:187 unstable:0
Feb 21 21:20:25 host kernel: [474990.053517] free:2085 slab_reclaimable:3388 slab_unreclaimable:4094
Feb 21 21:20:25 host kernel: [474990.053519] mapped:16336 shmem:72054 pagetables:10109 bounce:0
Feb 21 21:20:25 host kernel: [474990.053553] Node 0 DMA free:4036kB min:60kB low:72kB high:88kB active_anon:4960kB inactive_anon:5100kB active_file:84kB inactive_file:120kB unevictable:0kB isolated(anon):384kB isolated(file):0kB present:15372kB mlocked:0kB dirty:0kB writeback:0kB mapped:1036kB shmem:2908kB slab_reclaimable:364kB slab_unreclaimable:168kB kernel_stack:80kB pagetables:312kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:128 all_unreclaimable? no
Feb 21 21:20:25 host kernel: [474990.053569] lowmem_reserve[]: 0 994 994 994
Feb 21 21:20:25 host kernel: [474990.053574] Node 0 DMA32 free:4304kB min:4000kB low:5000kB high:6000kB active_anon:454868kB inactive_anon:455000kB active_file:1828kB inactive_file:1048kB unevictable:0kB isolated(anon):5888kB isolated(file):0kB present:1018072kB mlocked:0kB dirty:0kB writeback:748kB mapped:64308kB shmem:285308kB slab_reclaimable:13188kB slab_unreclaimable:16208kB kernel_stack:1648kB pagetables:40124kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:3698 all_unreclaimable? yes
Feb 21 21:20:25 host kernel: [474990.053588] lowmem_reserve[]: 0 0 0 0
Feb 21 21:20:25 host kernel: [474990.053593] Node 0 DMA: 116*4kB 171*8kB 25*16kB 6*32kB 3*64kB 3*128kB 2*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 4024kB
Feb 21 21:20:25 host kernel: [474990.053606] Node 0 DMA32: 402*4kB 135*8kB 43*16kB 5*32kB 2*64kB 1*128kB 0*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 4304kB
Feb 21 21:20:25 host kernel: [474990.053619] 97157 total pagecache pages
Feb 21 21:20:25 host kernel: [474990.053621] 24342 pages in swap cache
Feb 21 21:20:25 host kernel: [474990.053624] Swap cache stats: add 30122162, delete 30097820, find 7157191/10380822
Feb 21 21:20:25 host kernel: [474990.053627] Free swap = 0kB
Feb 21 21:20:25 host kernel: [474990.053629] Total swap = 2007032kB
Feb 21 21:20:25 host kernel: [474990.059436] 262142 pages RAM
Feb 21 21:20:25 host kernel: [474990.059439] 5429 pages reserved
Feb 21 21:20:25 host kernel: [474990.059441] 39879 pages shared
Feb 21 21:20:25 host kernel: [474990.059443] 229854 pages non-shared
Feb 21 21:21:36 host kernel: [475068.584297] php5-cgi invoked oom-killer: gfp_mask=0x200da, order=0, oom_adj=0
Feb 21 21:21:36 host kernel: [475068.584303] php5-cgi cpuset=/ mems_allowed=0
Feb 21 21:21:36 host kernel: [475068.584308] Pid: 23008, comm: php5-cgi Not tainted 2.6.32-5-amd64 #1
Feb 21 21:21:36 host kernel: [475068.584310] Call Trace:
Feb 21 21:21:36 host kernel: [475068.584320] [<ffffffff810b643c>] ? oom_kill_process+0x7f/0x23f
Feb 21 21:21:36 host kernel: [475068.584325] [<ffffffff8106bb5e>] ? timekeeping_get_ns+0xe/0x2e
Feb 21 21:21:36 host kernel: [475068.584328] [<ffffffff810b6960>] ? __out_of_memory+0x12a/0x141
Feb 21 21:21:36 host kernel: [475068.584330] [<ffffffff810b6ab7>] ? out_of_memory+0x140/0x172
Feb 21 21:21:36 host kernel: [475068.584333] [<ffffffff810ba81c>] ? __alloc_pages_nodemask+0x4ec/0x5fc
Feb 21 21:21:36 host kernel: [475068.584338] [<ffffffff810d8fd4>] ? read_swap_cache_async+0x5d/0xf3
Feb 21 21:21:36 host kernel: [475068.584341] [<ffffffff810d90c1>] ? swapin_readahead+0x57/0x98
Feb 21 21:21:36 host kernel: [475068.584345] [<ffffffff810b42db>] ? find_get_page+0x1a/0x77
Feb 21 21:21:36 host kernel: [475068.584348] 

```
And here some of my syslog:

```

pagecache pages
Feb 22 07:53:49 host kernel: [513000.178966] 4062 pages in swap cache
Feb 22 07:53:49 host kernel: [513000.178968] Swap cache stats: add 42026848, delete 42022786, find 7900579/12351861
Feb 22 07:53:49 host kernel: [513000.178969] Free swap = 0kB
Feb 22 07:53:49 host kernel: [513000.178971] Total swap = 2007032kB
Feb 22 07:53:49 host kernel: [513000.182850] 262142 pages RAM
Feb 22 07:53:49 host kernel: [513000.182853] 5429 pages reserved
Feb 22 07:53:49 host kernel: [513000.182855] 29924 pages shared
Feb 22 07:53:49 host kernel: [513000.182856] 228753 pages non-shared
Feb 22 07:53:49 host kernel: [513000.182860] Out of memory: kill process 4834 (php5-cgi) score 114926 or a child
Feb 22 07:53:49 host kernel: [513000.183906] Killed process 13185 (php5-cgi)
Feb 22 07:53:49 host kernel: [513000.205134] php5-cgi invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0
Feb 22 07:53:49 host kernel: [513000.205139] php5-cgi cpuset=/ mems_allowed=0
Feb 22 07:53:49 host kernel: [513000.205143] Pid: 13188, comm: php5-cgi Not tainted 2.6.32-5-amd64 #1
Feb 22 07:53:49 host kernel: [513000.205145] Call Trace:
Feb 22 07:53:49 host kernel: [513000.205155] [<ffffffff810b643c>] ? oom_kill_process+0x7f/0x23f
Feb 22 07:53:49 host kernel: [513000.205159] [<ffffffff810b6960>] ? __out_of_memory+0x12a/0x141
Feb 22 07:53:49 host kernel: [513000.205161] [<ffffffff810b6ab7>] ? out_of_memory+0x140/0x172
Feb 22 07:53:49 host kernel: [513000.205165] [<ffffffff810ba81c>] ? __alloc_pages_nodemask+0x4ec/0x5fc
Feb 22 07:53:49 host kernel: [513000.205169] [<ffffffff810bbd85>] ? __do_page_cache_readahead+0x9b/0x1b4
Feb 22 07:53:49 host kernel: [513000.205172] [<ffffffff810bbeba>] ? ra_submit+0x1c/0x20
Feb 22 07:53:49 host kernel: [513000.205175] [<ffffffff810b4b87>] ? filemap_fault+0x17d/0x2f6
Feb 22 07:53:49 host kernel: [513000.205180] [<ffffffff810cab26>] ? __do_fault+0x54/0x3c3
Feb 22 07:53:49 host kernel: [513000.205182] [<ffffffff810cce7a>] ? handle_mm_fault+0x3b8/0x80f
Feb 22 07:53:49 host kernel: [513000.205188] [<ffffffff8101180e>] ? call_function_single_interrupt+0xe/0x20
Feb 22 07:53:49 host kernel: [513000.205194] [<ffffffff812ff306>] ? do_page_fault+0x2e0/0x2fc
Feb 22 07:53:49 host kernel: [513000.205197] [<ffffffff812fd1a5>] ? page_fault+0x25/0x30
Feb 22 07:53:49 host kernel: [513000.205199] Mem-Info:
Feb 22 07:53:49 host kernel: [513000.205200] Node 0 DMA per-cpu:
Feb 22 07:53:49 host kernel: [513000.205208] CPU 0: hi: 0, btch: 1 usd: 0
Feb 22 07:53:49 host kernel: [513000.205210] CPU 1: hi: 0, btch: 1 usd: 0
Feb 22 07:53:49 host kernel: [513000.205211] Node 0 DMA32 per-cpu:
Feb 22 07:53:49 host kernel: [513000.205213] CPU 0: hi: 186, btch: 31 usd: 30
Feb 22 07:53:49 host kernel: [513000.205215] CPU 1: hi: 186, btch: 31 usd: 26
Feb 22 07:53:49 host kernel: [513000.205219] active_anon:107971 inactive_anon:110325 isolated_anon:9
Feb 22 07:53:49 host kernel: [513000.205220] active_file:43 inactive_file:111 isolated_file:0
Feb 22 07:53:49 host kernel: [513000.205221] unevictable:0 dirty:0 writeback:0 unstable:0
Feb 22 07:53:49 host kernel: [513000.205221] free:1998 slab_reclaimable:3374 slab_unreclaimable:6288
Feb 22 07:53:49 host kernel: [513000.205222] mapped:1813 shmem:108269 pagetables:20249 bounce:0
Feb 22 07:53:49 host kernel: [513000.205224] Node 0 DMA free:4028kB min:60kB low:72kB high:88kB active_anon:3140kB inactive_anon:3420kB active_file:28kB inactive_file:28kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15372kB mlocked:0kB dirty:0kB writeback:0kB mapped:168kB shmem:2444kB slab_reclaimable:508kB slab_unreclaimable:912kB kernel_stack:1232kB pagetables:1744kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
Feb 22 07:53:49 host kernel: [513000.205234] lowmem_reserve[]: 0 994 994 994
Feb 22 07:53:49 host kernel: [513000.205237] Node 0 DMA32 free:3964kB min:4000kB low:5000kB high:6000kB active_anon:428744kB inactive_anon:437880kB active_file:144kB inactive_file:416kB unevictable:0kB isolated(anon):36kB isolated(file):0kB present:1018072kB mlocked:0kB dirty:0kB writeback:0kB mapped:7084kB shmem:430632kB slab_reclaimable:12988kB slab_unreclaimable:24240kB kernel_stack:2144kB pagetables:79252kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:320 all_unreclaimable? no
Feb 22 07:53:49 host kernel: [513000.205247] lowmem_reserve[]: 0 0 0 0
Feb 22 07:53:49 host kernel: [513000.205249] Node 0 DMA: 642*4kB 2*8kB 4*16kB 5*32kB 7*64kB 4*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 4024kB
Feb 22 07:53:49 host kernel: [513000.205256] Node 0 DMA32: 507*4kB 128*8kB 5*16kB 6*32kB 2*64kB 0*128kB 0*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 3964kB
Feb 22 07:53:49 host kernel: [513000.205267] 112524 total pagecache pages
Feb 22 07:53:49 host kernel: [513000.205268] 4062 pages in swap cache
Feb 22 07:53:49 host kernel: [513000.205270] Swap cache stats: add 42026848, delete 42022786, find 7900579/12351861
Feb 22 07:53:49 host kernel: [513000.205271] Free swap = 0kB
Feb 22 07:53:49 host kernel: [513000.205272] Total swap = 2007032kB
Feb 22 07:53:49 host kernel: [513000.208788] 262142 pages RAM
Feb 22 07:53:49 host kernel: [513000.208790] 5429 pages reserved
Feb 22 07:53:49 host kernel: [513000.208792] 29212 pages shared
Feb 22 07:53:49 host kernel: [513000.208793] 228505 pages non-shared
Feb 22 07:53:49 host kernel: [513000.208796] Out of memory: kill process 4832 (php5-cgi) score 86194 or a child
Feb 22 07:53:49 host kernel: [513000.209503] Killed process 13184 (php5-cgi)
Feb 22 07:53:49 host kernel: [513000.216462] find invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0
Feb 22 07:53:49 host kernel: [513000.216467] find cpuset=/ mems_allowed=0
Feb 22 07:53:49 host kernel: [513000.216471] Pid: 13104, comm: find Not tainted 2.6.32-5-amd64 #1
Feb 22 07:53:49 host kernel: [513000.216473] Call Trace:
Feb 22 07:53:49 host kernel: [513000.216483] [<ffffffff810b643c>] ? oom_kill_process+0x7f/0x23f
Feb 22 07:53:49 host kernel: [513000.216488] [<ffffffff8106bb5e>] ? timekeeping_get_ns+0xe/0x2e
Feb 22 07:53:49 host kernel: [513000.216491] [<ffffffff810b6960>] ? __out_of_memory+0x12a/0x141
Feb 22 07:53:49 host kernel: [513000.216494] [<ffffffff810b6ab7>] ? out_of_memory+0x140/0x172
Feb 22 07:53:49 host kernel: [513000.216497] [<ffffffff810ba81c>] ? __alloc_pages_nodemask+0x4ec/0x5fc
Feb 22 07:53:49 host kernel: [513000.216503] [<ffffffff812fbb8a>] ? io_schedule+0x93/0xb7
Feb 22 07:53:49 host kernel: [513000.216507] [<ffffffff810bbd85>] ? __do_page_cache_readahead+0x9b/0x1b4
Feb 22 07:53:49 host kernel: [513000.216511] [<ffffffff81065074>] ? wake_bit_function+0x0/0x23
Feb 22 07:53:49 host kernel: [513000.216514] [<ffffffff810bbeba>] ? ra_submit+0x1c/0x20
Feb 22 07:53:49 host kernel: [513000.216516] [<ffffffff810b4b87>] ? filemap_fault+0x17d/0x2f6
Feb 22 07:53:49 host kernel: [513000.216521] [<ffffffff810cab26>] ? __do_fault+0x54/0x3c3
Feb 22 07:53:49 host kernel: [513000.216524] [<ffffffff810cce7a>] ? handle_mm_fault+0x3b8/0x80f
Feb 22 07:53:49 host kernel: [513000.216527] [<ffffffff812ff306>] ? do_page_fault+0x2e0/0x2fc
Feb 22 07:53:49 host kernel: [513000.216530] [<ffffffff812fd1a5>] ? page_fault+0x25/0x30
Feb 22 07:53:49 host kernel: [513000.216532] Mem-Info:
Feb 22 07:53:49 host kernel: [513000.216533] Node 0 DMA per-cpu:
Feb 22 07:53:49 host kernel: [513000.216536] CPU 0: hi: 0, btch: 1 usd: 0
Feb 22 07:53:49 host kernel: [513000.216538] CPU 1: hi: 0, btch: 1 usd: 0
Feb 22 07:53:49 host kernel: [513000.216539] Node 0 DMA32 per-cpu:
Feb 22 07:53:49 host kernel: [513000.216541] CPU 0: hi: 186, btch: 31 usd: 71
Feb 22 07:53:49 host kernel: [513000.216543] CPU 1: hi: 186, btch: 31 usd: 61
Feb 22 07:53:49 host kernel: [513000.216547] active_anon:107971 inactive_anon:110325 isolated_anon:9
Feb 22 07:53:49 host kernel: [513000.216548] active_file:66 inactive_file:96 isolated_file:44
Feb 22 07:53:49 host kernel: [513000.216549] unevictable:0 dirty:0 writeback:0 unstable:0
Feb 22 07:53:49 host kernel: [513000.216550] free:1982 slab_reclaimable:3374 slab_unreclaimable:6288
Feb 22 07:53:49 host kernel: [513000.216551] mapped:1813 shmem:108269 pagetables:20199 bounce:0
Feb 22 07:53:49 host kernel: [513000.216553] Node 0 DMA free:4028kB min:60kB low:72kB high:88kB active_anon:3140kB inactive_anon:3420kB active_file:20kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15372kB mlocked:0kB dirty:0kB writeback:0kB mapped:168kB shmem:2444kB slab_reclaimable:508kB slab_unreclaimable:912kB kernel_stack:1232kB pagetables:1744kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
Feb 22 07:53:49 host kernel: [513000.216562] lowmem_reserve[]: 0 994 994 994
Feb 22 07:53:49 host kernel: [513000.216565] Node 0 DMA32 free:3900kB min:4000kB low:5000kB high:6000kB active_anon:428744kB inactive_anon:437880kB active_file:244kB inactive_file:384kB unevictable:0kB isolated(anon):36kB isolated(file):176kB present:1018072kB mlocked:0kB dirty:0kB writeback:0kB mapped:7084kB shmem:430632kB slab_reclaimable:12988kB slab_unreclaimable:24240kB kernel_stack:2144kB pagetables:79052kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:3040 all_unreclaimable? no
Feb 22 07:53:49 host kernel: [513000.216576] lowmem_reserve[]: 0 0 0 0
Feb 22 07:53:49 host kernel: [513000.216579] Node 0 DMA: 642*4kB 2*8kB 4*16kB 5*32kB 7*64kB 4*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 4024kB
Feb 22 07:53:49 host kernel: [513000.216589] Node 0 DMA32: 491*4kB 128*8kB 5*16kB 6*32kB 2*64kB 0*128kB 0*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 3900kB
Feb 22 07:53:49 host kernel: [513000.216598] 112549 total pagecache pages
Feb 22 07:53:49 host kernel: [513000.216600] 4062 pages in swap cache
Feb 22 07:53:49 host kernel: [513000.216603] Swap cache stats: add 42026848, delete 42022786, find 7900579/12351861
Feb 22 07:53:49 host kernel: [513000.216605] Free swap = 0kB
Feb 22 07:53:49 host kernel: [513000.216606] Total swap = 2007032kB
Feb 22 07:53:49 host kernel: [513000.220127] 262142 pages RAM
Feb 22 07:53:49 host kernel: [513000.220129] 5429 pages reserved
Feb 22 07:53:49 host kernel: [513000.220130] 28347 pages shared
Feb 22 07:53:49 host kernel: [513000.220131] 229347 pages non-shared
Feb 22 07:53:49 host kernel: [513000.220134] Out of memory: kill process 4834 (php5-cgi) score 86194 or a child
Feb 22 07:53:49 host kernel: [513000.220738] Killed process 13187 (php5-cgi)
Feb 22 07:53:49 host kernel: [513000.312547] rs:main Q:Reg invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0
Feb 22 07:53:49 host kernel: [513000.312556] rs:main Q:Reg cpuset=/ mems_allowed=0
Feb 22 07:53:49 host kernel: [513000.312563] Pid: 12603, comm: rs:main Q:Reg Not tainted 2.6.32-5-amd64 #1
Feb 22 07:53:49 host kernel: [513000.312566] Call Trace:
Feb 22 07:53:49 host kernel: [513000.312581] [<ffffffff810b643c>] ? oom_kill_process+0x7f/0x23f
Feb 22 07:53:49 host kernel: [513000.312590] [<ffffffff8106bb5e>] ? timekeeping_get_ns+0xe/0x2e
Feb 22 07:53:49 host kernel: [513000.312596] [<ffffffff810b6960>] ? __out_of_memory+0x12a/0x141
Feb 22 07:53:49 host kernel: [513000.312601] [<ffffffff810b6ab7>] ? out_of_memory+0x140/0x172
Feb 22 07:53:49 host kernel: [513000.312608] [<ffffffff810ba81c>] ? __alloc_pages_nodemask+0x4ec/0x5fc
Feb 22 07:53:49 host kernel: [513000.312616] [<ffffffff810bbd85>] ? __do_page_cache_readahead+0x9b/0x1b4
Feb 22 07:53:49 host kernel: [513000.312625] [<ffffffff810bbeba>] ? ra_submit+0x1c/0x20
Feb 22 07:53:49 host kernel: [513000.312632] [<ffffffff810b4b87>] ? filemap_fault+0x17d/0x2f6
Feb 22 07:53:49 host kernel: [513000.312642] [<ffffffff810cab26>] ? __do_fault+0x54/0x3c3
Feb 22 07:53:49 host kernel: [513000.312651] [<ffffffff810eef4e>] ? do_sync_write+0xce/0x113
Feb 22 07:53:49 host kernel: [513000.312658] [<ffffffff810cce7a>] ? handle_mm_fault+0x3b8/0x80f
Feb 22 07:53:49 host kernel: [513000.312670] [<ffffffff812ff306>] ? do_page_fault+0x2e0/0x2fc
Feb 22 07:53:49 host kernel: [513000.312678] [<ffffffff812fd1a5>] ? page_fault+0x25/0x30
Feb 22 07:53:49 host kernel: [513000.312683] Mem-Info:
Feb 22 07:53:49 host kernel: [513000.312687] Node 0 DMA per-cpu:
Feb 22 07:53:49 host kernel: [513000.312694] CPU 0: hi: 0, btch: 1 usd: 0
Feb 22 07:53:49 host kernel: [513000.312699] CPU 1: hi: 0, btch: 1 usd: 0
Feb 22 07:53:49 host kernel: [513000.312703] Node 0 DMA32 per-cpu:
Feb 22 07:53:49 host kernel: [513000.312707] CPU 0: hi: 186, btch: 31 usd: 0
Feb 22 07:53:49 host kernel: [513000.312711] CPU 1: hi: 186, btch: 31 usd: 60
Feb 22 07:53:49 host kernel: [513000.312719] active_anon:107946 inactive_anon:110325 isolated_anon:9
Feb 22 07:53:49 host kernel: [513000.312720] active_file:41 inactive_file:110 isolated_file:76
Feb 22 07:53:49 host kernel: [513000.312730] unevictable:0 dirty:0 writeback:0 unstable:0
Feb 22 07:53:49 host kernel: [513000.312732] free:2050 slab_reclaimable:3374 slab_unreclaimable:6288
Feb 22 07:53:49 host kernel: [513000.312734] mapped:1863 shmem:108269 pagetables:20199 bounce:0
Feb 22 07:53:49 host kernel: [513000.312738] Node 0 DMA free:4048kB min:60kB low:72kB high:88kB active_anon:3140kB inactive_anon:3420kB active_file:0kB inactive_file:48kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15372kB mlocked:0kB dirty:0kB writeback:0kB mapped:168kB shmem:2444kB slab_reclaimable:508kB slab_unreclaimable:912kB kernel_stack:1232kB pagetables:1744kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
Feb 22 07:53:49 host kernel: [513000.312756] lowmem_reserve[]: 0 994 994 994
Feb 22 07:53:49 host kernel: [513000.312762] Node 0 DMA32 free:4152kB min:4000kB low:5000kB high:6000kB active_anon:428644kB inactive_anon:437880kB active_file:176kB inactive_file:392kB unevictable:0kB isolated(anon):36kB isolated(file):304kB present:1018072kB mlocked:0kB dirty:0kB writeback:0kB mapped:7284kB shmem:430632kB slab_reclaimable:12988kB slab_unreclaimable:24240kB kernel_stack:2144kB pagetables:79052kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:96 all_unreclaimable? no
Feb 22 07:53:49 host kernel: [513000.312781] lowmem_reserve[]: 0 0 0 0
Feb 22 07:53:49 host kernel: [513000.312786] Node 0 DMA: 648*4kB 2*8kB 4*16kB 5*32kB 7*64kB 4*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 4048kB
Feb 22 07:53:49 host kernel: [513000.312809] Node 0 DMA32: 554*4kB 128*8kB 5*16kB 6*32kB 2*64kB 0*128kB 0*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 4152kB
Feb 22 07:53:49 host kernel: [513000.312828] 112599 total pagecache pages
Feb 22 07:53:49 host kernel: [513000.312832] 4062 pages in swap cache
Feb 22 07:53:49 host kernel: [513000.312838] Swap cache stats: add 42026848, delete 42022786, find 7900579/12351861
Feb 22 07:53:49 host kernel: [513000.312842] Free swap = 0kB
Feb 22 07:53:49 host kernel: [513000.312845] Total swap = 2007032kB
Feb 22 07:53:49 host kernel: [513000.319149] 262142 pages RAM
Feb 22 07:53:49 host kernel: [513000.319154] 5429 pages reserved
Feb 22 07:53:49 host kernel: [513000.319157] 28478 pages shared
Feb 22 07:53:49 host kernel: [513000.319160] 230212 pages non-shared
Feb 22 07:53:49 host kernel: [513000.319168] Out of memory: kill process 4847 (php5-cgi) score 114926 or a child
Feb 22 07:53:49 host kernel: [513000.320488] Killed process 13186 (php5-cgi)
Feb 22 07:53:49 host kernel: [513000.431005] php5-cgi invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0
Feb 22 07:53:49 host kernel: [513000.431013] php5-cgi cpuset=/ mems_allowed=0
Feb 22 07:53:49 host kernel: [513000.431019] Pid: 13188, comm: php5-cgi Not tainted 2.6.32-5-amd64 #1
Feb 22 07:53:49 host kernel: [513000.431023] Call Trace:
Feb 22 07:53:49 host kernel: [513000.431039] [<ffffffff810b643c>] ? oom_kill_process+0x7f/0x23f
Feb 22 07:53:49 host kernel: [513000.431051] [<ffffffff8106bb5e>] ? timekeeping_get_ns+0xe/0x2e
Feb 22 07:53:49 host kernel: [513000.431058] [<ffffffff810b6960>] ? __out_of_memory+0x12a/0x141
Feb 22 07:53:49 host kernel: [513000.431065] [<ffffffff810b6ab7>] ? out_of_memory+0x140/0x172
Feb 22 07:53:49 host kernel: [513000.431074] [<ffffffff810ba81c>] ? __alloc_pages_nodemask+0x4ec/0x5fc
Feb 22 07:53:49 host kernel: [513000.431086] [<ffffffff812fbb8a>] ? io_schedule+0x93/0xb7
Feb 22 07:53:49 host kernel: [513000.431096] [<ffffffff810bbd85>] ? __do_page_cache_readahead+0x9b/0x1b4
Feb 22 07:53:49 host kernel: [513000.431164] [<ffffffff81065074>] ? wake_bit_function+0x0/0x23
Feb 22 07:53:49 host kernel: [513000.431170] [<ffffffff810bbeba>] ? ra_submit+0x1c/0x20
Feb 22 07:53:49 host kernel: [513000.431175] [<ffffffff810b4b87>] ? filemap_fault+0x17d/0x2f6
Feb 22 07:53:49 host kernel: [513000.431183] [<ffffffff810cab26>] ? __do_fault+0x54/0x3c3
Feb 22 07:53:49 host kernel: [513000.431188] [<ffffffff810cce7a>] ? handle_mm_fault+0x3b8/0x80f
Feb 22 07:53:49 host kernel: [513000.431197] [<ffffffff8101180e>] ? call_function_single_interrupt+0xe/0x20
Feb 22 07:53:49 host kernel: [513000.431207] [<ffffffff8105babf>] ? do_sigaction+0x7b/0x171
Feb 22 07:53:49 host kernel: [513000.431214] [<ffffffff812ff306>] ? do_page_fault+0x2e0/0x2fc
Feb 22 07:53:49 host kernel: [513000.431220] [<ffffffff812fd1a5>] ? page_fault+0x25/0x30
Feb 22 07:53:49 host kernel: [513000.431223] Mem-Info:
Feb 22 07:53:49 host kernel: [513000.431226] Node 0 DMA per-cpu:
Feb 22 07:53:49 host kernel: [513000.431231] CPU 0: hi: 0, btch: 1 usd: 0
Feb 22 07:53:49 host kernel: [513000.431234] CPU 1: hi: 0, btch: 1 usd: 0
Feb 22 07:53:49 host kernel: [513000.431237] Node 0 DMA32 per-cpu:
Feb 22 07:53:49 host kernel: [513000.431245] CPU 0: hi: 186, btch: 31 usd: 2
Feb 22 07:53:49 host kernel: [513000.431248] CPU 1: hi: 186, btch: 31 usd: 59
Feb 22 07:53:49 host kernel: [513000.431256] active_anon:107971 inactive_anon:110325 isolated_anon:0
Feb 22 07:53:49 host kernel: [513000.431258] active_file:80 inactive_file:173 isolated_file:0
Feb 22 07:53:49 host kernel: [513000.431260] unevictable:0 dirty:0 writeback:0 unstable:0
Feb 22 07:53:49 host kernel: [513000.431262] free:1964 slab_reclaimable:3374 slab_unreclaimable:6288
Feb 22 07:53:49 host kernel: [513000.431264] mapped:1863 shmem:108269 pagetables:20224 bounce:0
Feb 22 07:53:49 host kernel: [513000.431268] Node 0 DMA free:4028kB min:60kB low:72kB high:88kB active_anon:3140kB inactive_anon:3420kB active_file:0kB inactive_file:28kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15372kB mlocked:0kB dirty:0kB writeback:0kB mapped:168kB shmem:2444kB slab_reclaimable:508kB slab_unreclaimable:912kB kernel_stack:1232kB pagetables:1744kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
Feb 22 07:53:49 host kernel: [513000.431292] lowmem_reserve[]: 0 994 994 994
Feb 22 07:53:49 host kernel: [513000.431300] Node 0 DMA32 free:3828kB min:4000kB low:5000kB high:6000kB active_anon:428744kB inactive_anon:437880kB active_file:328kB inactive_file:664kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:1018072kB mlocked:0kB dirty:0kB writeback:0kB mapped:7284kB shmem:430632kB slab_reclaimable:12988kB slab_unreclaimable:24240kB kernel_stack:2144kB pagetables:79152kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:1056 all_unreclaimable? yes
Feb 22 07:53:49 host kernel: [513000.431326] lowmem_reserve[]: 0 0 0 0
Feb 22 07:53:49 host kernel: [513000.431333] Node 0 DMA: 639*4kB 5*8kB 4*16kB 5*32kB 7*64kB 4*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 4036kB
Feb 22 07:53:49 host kernel: [513000.431347] Node 0 DMA32: 473*4kB 128*8kB 5*16kB 6*32kB 2*64kB 0*128kB 0*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 3828kB
Feb 22 07:53:49 host kernel: [513000.431360] 112599 total pagecache pages
Feb 22 07:53:49 host kernel: [513000.431363] 4062 pages in swap cache
Feb 22 07:53:49 host kernel: [513000.431367] Swap cache stats: add 42026848, delete 42022786, find 7900579/12351861
Feb 22 07:53:49 host kernel: [513000.431370] Free swap = 0kB
Feb 22 07:53:49 host kernel: [513000.431372] Total swap = 2007032kB
Feb 22 07:53:49 host kernel: [513000.437334] 262142 pages RAM
Feb 22 07:53:49 host kernel: [513000.437339] 5429 pages reserved
Feb 22 07:53:49 host kernel: [513000.437342] 29058 pages shared
Feb 22 07:53:49 host kernel: [513000.437344] 229440 pages non-shared
Feb 22 07:53:49 host kernel: [513000.437351] Out of memory: kill process 4832 (php5-cgi) score 86194 or a child
Feb 22 07:53:49 host kernel: [513000.439138] Killed process 13190 (php5-cgi)
Feb 22 07:53:49 host kernel: [513000.448545] Out of memory: kill process 4847 (php5-cgi) score 86194 or a child
Feb 22 07:53:49 host kernel: [513000.449720] Killed process 13189 (php5-cgi)
Feb 22 07:53:49 host kernel: [513000.456570] Out of memory: kill process 4849 (php5-cgi) score 86194 or a child
Feb 22 07:53:49 host kernel: [513000.457843] Killed process 13188 (php5-cgi)
Feb 22 07:53:49 host kernel: [513000.578675] Out of memory: kill

```

---

### Post by matt_symes on 2013-02-24
Hi
```

Feb 21 21:20:25 host kernel: [474990.053408] Pid: 23168, comm: php5-cgi Not tainted 2.6.32-5-amd64 #1
Feb 21 21:20:25 host kernel: [474990.053412] Call Trace:
Feb 21 21:20:25 host kernel: [474990.053424] [<ffffffff810b643c>] ? oom_kill_process+0x7f/0x23f
```

You have a problem with php. Disable it for a while and see if you still get the same problems.

Once you have proved it's php and discounted other things you can then look at what is wrong with it.

Kind regards

---

