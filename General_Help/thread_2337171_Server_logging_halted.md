---
title: "Server logging halted"
date: 2016-09-15
forum: General Help
---

### Post by karhulitos on 2016-09-15
Hi,

this post is related to [https://ubuntuforums.org/showthread.php?t=2336783]("https://ubuntuforums.org/showthread.php?t=2336783"). Trying to understand why that happened I wanted to read some logs.
For my surprise I couldn't find icecast access log entries for evening of Sep 10th. I also noticed that icecast had crashed. 3 days later than the actual load peak (evening of Sept 10).

```
:/var/log$ grep "Sep 13 08:" /var/log/syslog.2
Sep 13 08:46:02 railers kernel: [1174606.629170] apache2 invoked oom-killer: gfp_mask=0x201da, order=0, oom_score_adj=0
Sep 13 08:46:02 railers kernel: [1174606.629178] apache2 cpuset=/ mems_allowed=0
Sep 13 08:46:02 railers kernel: [1174606.629183] CPU: 2 PID: 21230 Comm: apache2 Not tainted 3.13.0-74-generic #118-Ubuntu
Sep 13 08:46:02 railers kernel: [1174606.629184] Hardware name: QEMU Standard PC (i440FX + PIIX, 1996), BIOS rel-1.7.5.1-0-g8936dbb-20141113_115728-nilsson.home.kraxel.org 04/01/2014
Sep 13 08:46:02 railers kernel: [1174606.629186]  0000000000000000 ffff880034b01980 ffffffff81724b70 ffff880033196000
Sep 13 08:46:02 railers kernel: [1174606.629189]  ffff880034b01a08 ffffffff8171f177 0000000000000000 0000000000000000
Sep 13 08:46:02 railers kernel: [1174606.629191]  ffff88003499cba0 0000000000040004 000000000004df8f 0000000000000000
Sep 13 08:46:02 railers kernel: [1174606.629193] Call Trace:
Sep 13 08:46:02 railers kernel: [1174606.629220]  [<ffffffff81724b70>] dump_stack+0x45/0x56
Sep 13 08:46:02 railers kernel: [1174606.629223]  [<ffffffff8171f177>] dump_header+0x7f/0x1f1
Sep 13 08:46:02 railers kernel: [1174606.629239]  [<ffffffff8115308e>] oom_kill_process+0x1ce/0x330
Sep 13 08:46:02 railers kernel: [1174606.629254]  [<ffffffff812d85a5>] ? security_capable_noaudit+0x15/0x20
Sep 13 08:46:02 railers kernel: [1174606.629256]  [<ffffffff811537c4>] out_of_memory+0x414/0x450
Sep 13 08:46:02 railers kernel: [1174606.629260]  [<ffffffff81159b00>] __alloc_pages_nodemask+0xa60/0xb80
Sep 13 08:46:02 railers kernel: [1174606.629270]  [<ffffffff81198073>] alloc_pages_current+0xa3/0x160
Sep 13 08:46:02 railers kernel: [1174606.629276]  [<ffffffff8114fc47>] __page_cache_alloc+0x97/0xc0
Sep 13 08:46:02 railers kernel: [1174606.629292]  [<ffffffff81151655>] filemap_fault+0x185/0x410
Sep 13 08:46:02 railers kernel: [1174606.629300]  [<ffffffff8117652f>] __do_fault+0x6f/0x530
Sep 13 08:46:02 railers kernel: [1174606.629303]  [<ffffffff8117a3b2>] handle_mm_fault+0x482/0xf10
Sep 13 08:46:02 railers kernel: [1174606.629309]  [<ffffffff81730cb4>] __do_page_fault+0x184/0x570
Sep 13 08:46:02 railers kernel: [1174606.629320]  [<ffffffff810a0605>] ? set_next_entity+0x95/0xb0
Sep 13 08:46:02 railers kernel: [1174606.629332]  [<ffffffff8101260b>] ? __switch_to+0x16b/0x4d0
Sep 13 08:46:02 railers kernel: [1174606.629335]  [<ffffffff817310ba>] do_page_fault+0x1a/0x70
Sep 13 08:46:02 railers kernel: [1174606.629338]  [<ffffffff8172dfa5>] ? do_device_not_available+0x35/0x50
Sep 13 08:46:02 railers kernel: [1174606.629340]  [<ffffffff8172d3e8>] page_fault+0x28/0x30
Sep 13 08:46:02 railers kernel: [1174606.629341] Mem-Info:
Sep 13 08:46:02 railers kernel: [1174606.629342] Node 0 DMA per-cpu:
Sep 13 08:46:02 railers kernel: [1174606.629344] CPU    0: hi:    0, btch:   1 usd:   0
Sep 13 08:46:02 railers kernel: [1174606.629345] CPU    1: hi:    0, btch:   1 usd:   0
Sep 13 08:46:02 railers kernel: [1174606.629346] CPU    2: hi:    0, btch:   1 usd:   0
Sep 13 08:46:02 railers kernel: [1174606.629347] CPU    3: hi:    0, btch:   1 usd:   0
Sep 13 08:46:02 railers kernel: [1174606.629348] Node 0 DMA32 per-cpu:
Sep 13 08:46:02 railers kernel: [1174606.629349] CPU    0: hi:  186, btch:  31 usd: 182
Sep 13 08:46:02 railers kernel: [1174606.629351] CPU    1: hi:  186, btch:  31 usd: 173
Sep 13 08:46:02 railers kernel: [1174606.629351] CPU    2: hi:  186, btch:  31 usd:  30
Sep 13 08:46:02 railers kernel: [1174606.629352] CPU    3: hi:  186, btch:  31 usd: 181
Sep 13 08:46:02 railers kernel: [1174606.629355] active_anon:113415 inactive_anon:115530 isolated_anon:0
Sep 13 08:46:02 railers kernel: [1174606.629355]  active_file:30 inactive_file:38 isolated_file:0
Sep 13 08:46:02 railers kernel: [1174606.629355]  unevictable:0 dirty:0 writeback:0 unstable:0
Sep 13 08:46:02 railers kernel: [1174606.629355]  free:12230 slab_reclaimable:2452 slab_unreclaimable:3498
Sep 13 08:46:02 railers kernel: [1174606.629355]  mapped:997 shmem:5129 pagetables:2811 bounce:0
Sep 13 08:46:02 railers kernel: [1174606.629355]  free_cma:0
Sep 13 08:46:02 railers kernel: [1174606.629358] Node 0 DMA free:4584kB min:704kB low:880kB high:1056kB active_anon:3868kB inactive_anon:6780kB active_file:0kB inactive_file:80kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15992kB managed:15908kB mlocked:0kB dirty:0kB writeback:0kB mapped:216kB shmem:296kB slab_reclaimable:52kB slab_unreclaimable:144kB kernel_stack:8kB pagetables:108kB unstable:0kB bounce:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:134 all_unreclaimable? yes
Sep 13 08:46:02 railers kernel: [1174606.629362] lowmem_reserve[]: 0 975 975 975
Sep 13 08:46:02 railers kernel: [1174606.629364] Node 0 DMA32 free:44336kB min:44348kB low:55432kB high:66520kB active_anon:449792kB inactive_anon:455340kB active_file:120kB inactive_file:72kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:1032064kB managed:1001500kB mlocked:0kB dirty:0kB writeback:0kB mapped:3772kB shmem:20220kB slab_reclaimable:9756kB slab_unreclaimable:13848kB kernel_stack:1240kB pagetables:11136kB unstable:0kB bounce:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:302 all_unreclaimable? yes
Sep 13 08:46:02 railers kernel: [1174606.629367] lowmem_reserve[]: 0 0 0 0
Sep 13 08:46:02 railers kernel: [1174606.629369] Node 0 DMA: 3*4kB (UEM) 10*8kB (UEM) 9*16kB (U) 7*32kB (UEM) 1*64kB (E) 4*128kB (UEM) 4*256kB (UEM) 1*512kB (E) 2*1024kB (EM) 0*2048kB 0*4096kB = 4620kB
Sep 13 08:46:02 railers kernel: [1174606.629377] Node 0 DMA32: 284*4kB (UEM) 177*8kB (UEM) 211*16kB (UEM) 196*32kB (UE) 115*64kB (UE) 62*128kB (UEM) 32*256kB (UEM) 17*512kB (UEM) 0*1024kB 0*2048kB 0*4096kB = 44392kB
Sep 13 08:46:02 railers kernel: [1174606.629386] Node 0 hugepages_total=0 hugepages_free=0 hugepages_surp=0 hugepages_size=2048kB
Sep 13 08:46:02 railers kernel: [1174606.629387] 5833 total pagecache pages
Sep 13 08:46:02 railers kernel: [1174606.629388] 549 pages in swap cache
Sep 13 08:46:02 railers kernel: [1174606.629389] Swap cache stats: add 495565, delete 495016, find 679691/717554
Sep 13 08:46:02 railers kernel: [1174606.629390] Free swap  = 0kB
Sep 13 08:46:02 railers kernel: [1174606.629391] Total swap = 260092kB
Sep 13 08:46:02 railers kernel: [1174606.629392] 262014 pages RAM
Sep 13 08:46:02 railers kernel: [1174606.629393] 0 pages HighMem/MovableOnly
Sep 13 08:46:02 railers kernel: [1174606.629393] 7641 pages reserved
Sep 13 08:46:02 railers kernel: [1174606.629394] [ pid ]   uid  tgid total_vm      rss nr_ptes swapents oom_score_adj name
Sep 13 08:46:02 railers kernel: [1174606.629399] [  308]     0   308     4868        0      13       89             0 upstart-udev-br
Sep 13 08:46:02 railers kernel: [1174606.629401] [  314]     0   314    12812        2      27      142         -1000 systemd-udevd
Sep 13 08:46:02 railers kernel: [1174606.629403] [  436]     0   436     3814        0      12       56             0 upstart-socket-
Sep 13 08:46:02 railers kernel: [1174606.629405] [  675]   102   675     9808        1      24      105             0 dbus-daemon
Sep 13 08:46:02 railers kernel: [1174606.629406] [  739]   101   739    64008     1177      32     1759             0 rsyslogd
Sep 13 08:46:02 railers kernel: [1174606.629408] [  748]     0   748     3851        0      13      103             0 upstart-file-br
Sep 13 08:46:02 railers kernel: [1174606.629410] [  757]     0   757    10861        2      26       90             0 systemd-logind
Sep 13 08:46:02 railers kernel: [1174606.629418] [  764]   108   764     8088       34      22       57             0 avahi-daemon
Sep 13 08:46:02 railers kernel: [1174606.629420] [  765]   108   765     8054        3      21       59             0 avahi-daemon
Sep 13 08:46:02 railers kernel: [1174606.629422] [  860]     0   860     3633        2      12       39             0 getty
Sep 13 08:46:02 railers kernel: [1174606.629424] [  864]     0   864     3633        2      13       37             0 getty
Sep 13 08:46:02 railers kernel: [1174606.629425] [  869]     0   869     3633        2      13       40             0 getty
Sep 13 08:46:02 railers kernel: [1174606.629427] [  870]     0   870     3633        1      12       39             0 getty
Sep 13 08:46:02 railers kernel: [1174606.629428] [  873]     0   873     3633        2      12       40             0 getty
Sep 13 08:46:02 railers kernel: [1174606.629430] [  910]     0   910    15344       36      34      133         -1000 sshd
Sep 13 08:46:02 railers kernel: [1174606.629432] [  937]     0   937     4783        3      13       40             0 atd
Sep 13 08:46:02 railers kernel: [1174606.629433] [  938]     0   938     5912       27      17       37             0 cron
Sep 13 08:46:02 railers kernel: [1174606.629435] [  948]   107   948   236074    30069     129    10073             0 mysqld
Sep 13 08:46:02 railers kernel: [1174606.629437] [  960]     0   960     1091        1       8       36             0 acpid
Sep 13 08:46:02 railers kernel: [1174606.629439] [  977]     0   977     4797       30      14       34             0 irqbalance
Sep 13 08:46:02 railers kernel: [1174606.629440] [ 1025]   106  1025   322206   158755     433    31576             0 icecast2
Sep 13 08:46:02 railers kernel: [1174606.629442] [ 1039]     0  1039   107382        0      26      580             0 osspd
Sep 13 08:46:02 railers kernel: [1174606.629444] [ 1088]   109  1088   168786     1172     145     1702             0 mpd
Sep 13 08:46:02 railers kernel: [1174606.629446] [ 1177]     0  1177    97106      173     124     1797             0 apache2
Sep 13 08:46:02 railers kernel: [1174606.629447] [ 1219]     0  1219     3633        2      12       38             0 getty
Sep 13 08:46:02 railers kernel: [1174606.629449] [ 7787]    33  7787   102138     2485     151     3114             0 apache2
Sep 13 08:46:02 railers kernel: [1174606.629451] [21230]    33 21230   100849     5867     148     1538             0 apache2
Sep 13 08:46:02 railers kernel: [1174606.629452] [29170]    33 29170   101081     1914     147     3580             0 apache2
Sep 13 08:46:02 railers kernel: [1174606.629454] [13590]    33 13590   103190     4494     154     1993             0 apache2
Sep 13 08:46:02 railers kernel: [1174606.629456] [22254]    33 22254    99851     1597     143     2642             0 apache2
Sep 13 08:46:02 railers kernel: [1174606.629457] [23745]    33 23745    99849     4592     148     1794             0 apache2
Sep 13 08:46:02 railers kernel: [1174606.629459] [26960]    33 26960    99847     2284     143     1959             0 apache2
Sep 13 08:46:02 railers kernel: [1174606.629461] [ 3229]    33  3229    99415     1799     132     2028             0 apache2
Sep 13 08:46:02 railers kernel: [1174606.629462] [ 9746]    33  9746    98864     1170     130     2176             0 apache2
Sep 13 08:46:02 railers kernel: [1174606.629464] [14608]    33 14608   101078     3601     144     1825             0 apache2
Sep 13 08:46:02 railers kernel: [1174606.629466] [ 9102]     0  9102    14908       70      35       44             0 cron
Sep 13 08:46:02 railers kernel: [1174606.629467] [ 9103]    33  9103     1110       25       6        2             0 sh
Sep 13 08:46:02 railers kernel: [1174606.629469] [ 9104]    33  9104    71069     4460     103      988             0 php
Sep 13 08:46:02 railers kernel: [1174606.629471] Out of memory: Kill process 1025 (icecast2) score 597 or sacrifice child
Sep 13 08:46:02 railers kernel: [1174606.629606] Killed process 1025 (icecast2) total-vm:1288824kB, anon-rss:635020kB, file-rss:0kB
Sep 13 08:46:11 railers CRON[9102]: (CRON) info (No MTA installed, discarding output)
```

Then I noticed I seem to be missing basically all log entries in syslog and kern.log of that same time region. I feel I am missing the whole SYSLOG file of that date (Sep 11 6:25). Syslog.3 starts from Sep 11  6:27 and Syslog.4 last line is Sep 10 6:25:01.
```
drwxr-xr-x  2 root      root        4096 Aug 28  2013 news
-rw-r-----  1 syslog    adm        22350 Sep 15 15:20 syslog
-rw-r-----  1 syslog    adm        59538 Sep 15 06:25 syslog.1
-rw-r-----  1 syslog    adm       124298 Sep 14 06:25 syslog.2
-rw-r-----  1 syslog    adm        59586 Sep 12 06:25 syslog.3
-rw-r-----  1 syslog    adm        59264 Sep 10 06:25 syslog.4
-rw-r-----  1 syslog    adm        60385 Sep  9 06:25 syslog.6
-rw-r-----  1 syslog    adm         2873 Sep  8 06:25 syslog.7.gz
-rw-r--r--  1 root      root      161039 Aug 30 18:29 udev

```

In case of running out of memory, would it be expected to have missing log entries in syslog, access.log and equivalent or completely missing log file(s)? First I though I had accidentally deleted icecast2's access.log but now that this same behavior appears on syslog too, I suspect something else than me. 
The lost data case I linked above I first suspected network outage but I am starting to feel there may be more to it.
The server is running on very low spec VM except I requested temporary 4vCPUs for the occasion. 1G of RAM. 20G disk (75% free). We had some 500 visitors accessing the server on Saturday evening, ~400 connected to icecast2 and approx 20 concurrent listeners over 7h of broadcast (18-01). I wouldn't think these are too much for the mini-VM but something definetively happened on Saturday evening - just can't read the logs to understand.

Pics from hypervisor console show rather stable behavior for the box Sep 10 between 18-01.

[edit] Just noticed I am completely missing syslog.5(.gz). What would cause that to happen if we exclude the possibility of me deleting it?
[edit2] this more and more looks like low memory condition and Ubuntu started to stop processes. Perhaps logging facility was one of those

[ATTACH=CONFIG]271198[/ATTACH][ATTACH=CONFIG]271199[/ATTACH]

---

