---
title: "mysql crash averaging 3 times a week - have to restart server"
date: 2015-06-22
forum: General Help
---

### Post by rob134 on 2015-06-22
About 2 or 3 times a week my database crashes. All my websites get the "error establishing a database connection" error - only way to solve this is to restart my linode since I'm unable to login ssh when this happens.


my Linode has: 1gb ram, ubuntu 14.04 with 256mb swap size. My apache/php/mysql configuration is according the Linode tutorials for 1gb ram.


This is the syslog of when it occured. It seems like it tries to kill processes in order to free up memory and because (after some research) it has 0 swap file size.
```
Jun 23 04:09:02 www CRON[26655]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Jun 23 04:09:18 www kernel: apache2 invoked oom-killer: gfp_mask=0x200da, order=0, oom_score_adj=0
Jun 23 04:09:18 www kernel: apache2 cpuset=/ mems_allowed=0
Jun 23 04:09:18 www kernel: CPU: 0 PID: 26613 Comm: apache2 Not tainted 4.0.5-x86_64-linode58 #1
Jun 23 04:09:18 www kernel: 0000000000000000 ffff8800029d67c0 ffffffff8193b626 ffff8800029d6180
Jun 23 04:09:18 www kernel: ffffffff819360a4 0000000000000400 ffff88003fe16000 0000000000000020
Jun 23 04:09:18 www kernel: ffff88003fe16000 0000000000000000 0000000000000000 0000000000000000
Jun 23 04:09:18 www kernel: Call Trace:
Jun 23 04:09:18 www kernel: [<ffffffff8193b626>] ? dump_stack+0x40/0x50
Jun 23 04:09:18 www kernel: [<ffffffff819360a4>] ? dump_header.isra.10+0x78/0x1e3
Jun 23 04:09:18 www kernel: [<ffffffff81941bb6>] ? _raw_spin_unlock_irqrestore+0x2e/0x3f
Jun 23 04:09:18 www kernel: [<ffffffff81172f4a>] ? oom_kill_process+0xbe/0x380
Jun 23 04:09:18 www kernel: [<ffffffff8117369a>] ? __out_of_memory+0x43d/0x47d
Jun 23 04:09:18 www kernel: [<ffffffff8117381b>] ? out_of_memory+0x52/0x67
Jun 23 04:09:18 www kernel: [<ffffffff811777e5>] ? __alloc_pages_nodemask+0x708/0x846
Jun 23 04:09:18 www kernel: [<ffffffff81004a2d>] ? __raw_callee_save_xen_pte_val+0x11/0x1e
Jun 23 04:09:18 www kernel: [<ffffffff811a57d6>] ? alloc_pages_vma+0x111/0x15a
Jun 23 04:09:18 www kernel: [<ffffffff8119fc14>] ? read_swap_cache_async+0x76/0x121
Jun 23 04:09:18 www kernel: [<ffffffff8119fe04>] ? swapin_readahead+0x145/0x155
Jun 23 04:09:18 www kernel: [<ffffffff811700bb>] ? find_get_entry+0x1a/0x68
Jun 23 04:09:18 www kernel: [<ffffffff81170b9f>] ? pagecache_get_page+0x26/0x160
Jun 23 04:09:18 www kernel: [<ffffffff8119365a>] ? handle_mm_fault+0x9c1/0xd80
Jun 23 04:09:18 www kernel: [<ffffffff8104219d>] ? __do_page_fault+0x321/0x37b
Jun 23 04:09:18 www kernel: [<ffffffff8193ec28>] ? __schedule+0x5de/0x7cd
Jun 23 04:09:18 www kernel: [<ffffffff81943f08>] ? page_fault+0x28/0x30
Jun 23 04:09:18 www kernel: Mem-Info:
Jun 23 04:09:18 www kernel: Node 0 DMA per-cpu:
Jun 23 04:09:18 www kernel: CPU    0: hi:    0, btch:   1 usd:   0
Jun 23 04:09:18 www kernel: Node 0 DMA32 per-cpu:
Jun 23 04:09:18 www kernel: CPU    0: hi:  186, btch:  31 usd:   5
Jun 23 04:09:18 www kernel: active_anon:104835 inactive_anon:104945 isolated_anon:0
Jun 23 04:09:18 www kernel: active_file:38 inactive_file:348 isolated_file:0
Jun 23 04:09:18 www kernel: unevictable:0 dirty:0 writeback:0 unstable:0
Jun 23 04:09:18 www kernel: free:2444 slab_reclaimable:17327 slab_unreclaimable:5466
Jun 23 04:09:18 www kernel: mapped:4636 shmem:5034 pagetables:2252 bounce:0
Jun 23 04:09:18 www kernel: free_cma:0
Jun 23 04:09:18 www kernel: Node 0 DMA free:3948kB min:60kB low:72kB high:88kB active_anon:4084kB inactive_anon:4224kB active_file:16kB inactive_file:24kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15996kB managed:15912kB mlocked:0kB dirty:0kB writeback:0kB mapped:836kB shmem:1152kB slab_reclaimable:864kB slab_unreclaimable:200kB kernel_stack:96kB pagetables:60kB unstable:0kB bounce:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:252 all_unreclaimable? yes
Jun 23 04:09:18 www kernel: lowmem_reserve[]: 0 968 968 968
Jun 23 04:09:18 www kernel: Node 0 DMA32 free:5828kB min:3948kB low:4932kB high:5920kB active_anon:415256kB inactive_anon:415556kB active_file:136kB inactive_file:1368kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:1032192kB managed:995724kB mlocked:0kB dirty:0kB writeback:0kB mapped:17708kB shmem:18984kB slab_reclaimable:68444kB slab_unreclaimable:21664kB kernel_stack:2848kB pagetables:8948kB unstable:0kB bounce:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:9264 all_unreclaimable? yes
Jun 23 04:09:18 www kernel: lowmem_reserve[]: 0 0 0 0
Jun 23 04:09:18 www kernel: Node 0 DMA: 13*4kB (UM) 10*8kB (UR) 11*16kB (R) 8*32kB (R) 5*64kB (R) 4*128kB (R) 2*256kB (R) 0*512kB 0*1024kB 1*2048kB (R) 0*4096kB = 3956kB
Jun 23 04:09:18 www kernel: Node 0 DMA32: 461*4kB (UEM) 122*8kB (UEMR) 30*16kB (MR) 17*32kB (R) 7*64kB (R) 2*128kB (R) 1*256kB (R) 0*512kB 1*1024kB (R) 0*2048kB 0*4096kB = 5828kB
Jun 23 04:09:18 www kernel: 7000 total pagecache pages
Jun 23 04:09:18 www kernel: 1563 pages in swap cache
Jun 23 04:09:18 www kernel: Swap cache stats: add 164053, delete 162490, find 242212/264237
**Jun 23 04:09:18 www kernel: Free swap  = 0kB**
Jun 23 04:09:18 www kernel: Total swap = 262140kB
Jun 23 04:09:18 www kernel: 262047 pages RAM
Jun 23 04:09:18 www kernel: 0 pages HighMem/MovableOnly
Jun 23 04:09:18 www kernel: 9138 pages reserved
Jun 23 04:09:18 www kernel: [ pid ]   uid  tgid total_vm      rss nr_ptes nr_pmds swapents oom_score_adj name
Jun 23 04:09:18 www kernel: [ 1554]     0  1554      919        0       4       1      230             0 upstart-udev-br
Jun 23 04:09:18 www kernel: [ 1561]     0  1561     2505        1       7       2      124         -1000 systemd-udevd
Jun 23 04:09:18 www kernel: [ 2477]     0  2477     1379       42       5       1      395             0 dhclient
Jun 23 04:09:18 www kernel: [ 2696]   105  2696     1060        0       6       2       77             0 dbus-daemon
Jun 23 04:09:18 www kernel: [ 2736]   101  2736     7752       72       9       2      213             0 rsyslogd
Jun 23 04:09:18 www kernel: [ 2745]     0  2745     1055        2       6       2       74             0 systemd-logind
Jun 23 04:09:18 www kernel: [ 2774]     0  2774      765       15       5       2       34             0 cron
Jun 23 04:09:18 www kernel: [ 2776]     0  2776     1951        1       7       1      121         -1000 sshd
Jun 23 04:09:18 www kernel: [ 2814]     0  2814      789        0       4       1      126             0 upstart-file-br
Jun 23 04:09:18 www kernel: [ 2815]     0  2815      851        0       5       1      199             0 upstart-socket-
Jun 23 04:09:18 www kernel: [ 2831]   104  2831    85771     6457      72       1    11904             0 mysqld
Jun 23 04:09:18 www kernel: [ 2853]     0  2853     8720     1524      17       2     2162             0 linode-longview
Jun 23 04:09:18 www kernel: [ 2914]     0  2914    31136      841      34       1      961             0 apache2
Jun 23 04:09:18 www kernel: [ 2986]     0  2986     9731      576      14       2      566             0 fail2ban-server
Jun 23 04:09:18 www kernel: [ 3026]     0  3026      606        1       5       2       27             0 getty
Jun 23 04:09:18 www kernel: [ 4462]     0  4462     1077        4       5       1       63             0 ntpd
Jun 23 04:09:18 www kernel: [ 4463]   103  4463     1046       21       5       1       43             0 ntpd
Jun 23 04:09:18 www kernel: [ 4802]     0  4802     3321        1      10       1      242             0 sshd
Jun 23 04:09:18 www kernel: [ 4840]  1001  4840     3321        0       9       1      242             0 sshd
Jun 23 04:09:18 www kernel: [ 4841]  1001  4841     1414        2       6       2       84             0 bash
Jun 23 04:09:18 www kernel: [ 4850]     0  4850     3294        0       9       1      218             0 sshd
Jun 23 04:09:18 www kernel: [ 4887]     0  4887     3294        1       8       1      226             0 sshd
Jun 23 04:09:18 www kernel: [ 4907]     0  4907     3335        1       9       1      247             0 sshd
Jun 23 04:09:18 www kernel: [ 4908]     0  4908     3424        1       9       1      294             0 sshd
Jun 23 04:09:18 www kernel: [ 4910]     0  4910     3423        1      10       1      291             0 sshd
Jun 23 04:09:18 www kernel: [ 4912]     0  4912     3336        1       9       1      248             0 sshd
Jun 23 04:09:18 www kernel: [ 4916]     0  4916     3335        1       9       1      277             0 sshd
Jun 23 04:09:18 www kernel: [ 4917]     0  4917     3424        1      10       1      297             0 sshd
Jun 23 04:09:18 www kernel: [ 4918]     0  4918     3336        1       9       1      248             0 sshd
Jun 23 04:09:18 www kernel: [ 4920]     0  4920     3336        1      10       1      270             0 sshd
Jun 23 04:09:18 www kernel: [ 5242]     0  5242     3294        1       9       1      232             0 sshd
Jun 23 04:09:18 www kernel: [ 5243]     0  5243     3294        1       8       1      233             0 sshd
Jun 23 04:09:18 www kernel: [ 5244]     0  5244     3294        1       9       1      233             0 sshd
Jun 23 04:09:18 www kernel: [ 5245]     0  5245     3293        1       9       1      232             0 sshd
Jun 23 04:09:18 www kernel: [ 5247]     0  5247     3293        0       9       1      230             0 sshd
Jun 23 04:09:18 www kernel: [ 5248]     0  5248     3294        1       8       1      233             0 sshd
Jun 23 04:09:18 www kernel: [ 5249]     0  5249     3294        1       8       1      233             0 sshd
Jun 23 04:09:18 www kernel: [ 5250]     0  5250     3293        1       8       1      232             0 sshd
Jun 23 04:09:18 www kernel: [ 6504]     0  6504     3319        1       9       1      239             0 sshd
Jun 23 04:09:18 www kernel: [ 6564]  1001  6564     3319        0       8       1      239             0 sshd
Jun 23 04:09:18 www kernel: [ 6565]  1001  6565     1411        1       7       2       82             0 bash
Jun 23 04:09:18 www kernel: [25014]    33 25014    41642    12866      82       1     3171             0 apache2
Jun 23 04:09:18 www kernel: [25659]    33 25659    39383    13394      78       1      632             0 apache2
Jun 23 04:09:18 www kernel: [25957]    33 25957    39999    13490      79       1     1002             0 apache2
Jun 23 04:09:18 www kernel: [26400]    33 26400    39188     9968      77       1     3742             0 apache2
Jun 23 04:09:18 www kernel: [26458]    33 26458    39328     9139      77       1     4478             0 apache2
Jun 23 04:09:18 www kernel: [26471]    33 26471    39158     9203      67       1     3690             0 apache2
Jun 23 04:09:18 www kernel: [26477]    33 26477    39237     8606      58       1     4674             0 apache2
Jun 23 04:09:18 www kernel: [26487]    33 26487    38906     9313      66       1     3349             0 apache2
Jun 23 04:09:18 www kernel: [26548]    33 26548    38992     8646      58       1     3761             0 apache2
Jun 23 04:09:18 www kernel: [26556]    33 26556    39402     7976      59       1     5365             0 apache2
Jun 23 04:09:18 www kernel: [26603]    33 26603    38660     6534      46       1     2150             0 apache2
Jun 23 04:09:18 www kernel: [26606]    33 26606    38546     7032      46       1     1567             0 apache2
Jun 23 04:09:18 www kernel: [26607]    33 26607    38542     7204      46       1     1470             0 apache2
Jun 23 04:09:18 www kernel: [26610]    33 26610    38332     7546      45       1      902             0 apache2
Jun 23 04:09:18 www kernel: [26611]    33 26611    38330     7587      45       1      925             0 apache2
Jun 23 04:09:18 www kernel: [26612]    33 26612    38402     7610      45       1      844             0 apache2
Jun 23 04:09:18 www kernel: [26613]    33 26613    38272     7648      45       1      776             0 apache2
Jun 23 04:09:18 www kernel: [26618]    33 26618    38394     7857      45       1      589             0 apache2
Jun 23 04:09:18 www kernel: [26619]    33 26619    38460     7895      46       1      601             0 apache2
Jun 23 04:09:18 www kernel: [26620]    33 26620    38265     7766      45       1      609             0 apache2
Jun 23 04:09:18 www kernel: [26621]    33 26621    38336     7803      46       1      611             0 apache2
Jun 23 04:09:18 www kernel: [26622]    33 26622    38208     7745      45       1      602             0 apache2
Jun 23 04:09:18 www kernel: [26623]    33 26623    38272     7762      45       1      593             0 apache2
Jun 23 04:09:18 www kernel: [26624]    33 26624    38079     7614      45       1      586             0 apache2
Jun 23 04:09:18 www kernel: [26625]    33 26625    38009     7585      45       1      586             0 apache2
Jun 23 04:09:18 www kernel: [26631]    33 26631    37494     7152      44       1      598             0 apache2
Jun 23 04:09:18 www kernel: [26632]    33 26632    37815     7340      45       1      594             0 apache2
Jun 23 04:09:18 www kernel: [26633]    33 26633    37753     7305      44       1      594             0 apache2
Jun 23 04:09:18 www kernel: [26635]    33 26635    37433     6984      44       1      594             0 apache2
Jun 23 04:09:18 www kernel: [26640]    33 26640    31154      419      29       1      942             0 apache2
Jun 23 04:09:18 www kernel: [26641]    33 26641    31144      399      27       1      951             0 apache2
Jun 23 04:09:18 www kernel: [26642]    33 26642    31144      399      27       1      951             0 apache2
Jun 23 04:09:18 www kernel: [26643]    33 26643    31144      399      27       1      951             0 apache2
Jun 23 04:09:18 www kernel: [26644]    33 26644    31144      399      27       1      951             0 apache2
Jun 23 04:09:18 www kernel: [26645]    33 26645    31144      399      27       1      951             0 apache2
Jun 23 04:09:18 www kernel: [26646]    33 26646    31144      399      27       1      951             0 apache2
Jun 23 04:09:18 www kernel: [26647]    33 26647    31144      399      27       1      951             0 apache2
Jun 23 04:09:18 www kernel: [26648]    33 26648    31144      399      27       1      951             0 apache2
Jun 23 04:09:18 www kernel: [26650]    33 26650    31144      399      27       1      951             0 apache2
**Jun 23 04:09:18 www kernel: Out of memory: Kill process 2831 (mysqld) score 57 or sacrifice child**
Jun 23 04:09:18 www kernel: Killed process 2831 (mysqld) total-vm:343084kB, anon-rss:25828kB, file-rss:0kB
Jun 23 04:09:18 www kernel: init: mysql main process (2831) killed by KILL signal
Jun 23 04:09:18 www kernel: init: mysql main process ended, respawning
Jun 23 04:09:19 www kernel: init: mysql main process (26693) terminated with status 1
Jun 23 04:09:19 www kernel: init: mysql main process ended, respawning
Jun 23 04:09:19 www kernel: init: mysql post-start process (26694) terminated with status 1
Jun 23 04:09:20 www kernel: init: mysql main process (26728) terminated with status 1
Jun 23 04:09:20 www kernel: init: mysql respawning too fast, stopped
```


the error log from /var/log/mysql shows:
```
150623  4:09:18 [Warning] Using unique option prefix myisam-recover instead of myisam-recover-options is deprecated and will be removed in a future release. Please use the full name instead.
150623  4:09:18 [Note] Plugin 'FEDERATED' is disabled.
150623  4:09:18 InnoDB: The InnoDB memory heap is disabled
150623  4:09:18 InnoDB: Mutexes and rw_locks use GCC atomic builtins
150623  4:09:18 InnoDB: Compressed tables use zlib 1.2.8
150623  4:09:18 InnoDB: Using Linux native AIO
150623  4:09:18 InnoDB: Initializing buffer pool, size = 128.0M
InnoDB: mmap(135987200 bytes) failed; errno 12
150623  4:09:18 InnoDB: Completed initialization of buffer pool
150623  4:09:18 InnoDB: Fatal error: cannot allocate memory for the buffer pool
150623  4:09:18 [ERROR] Plugin 'InnoDB' init function returned error.
150623  4:09:18 [ERROR] Plugin 'InnoDB' registration as a STORAGE ENGINE failed.
150623  4:09:18 [ERROR] Unknown/unsupported storage engine: InnoDB
150623  4:09:18 [ERROR] Aborting


150623  4:09:18 [Note] /usr/sbin/mysqld: Shutdown complete


150623  4:09:19 [Warning] Using unique option prefix myisam-recover instead of myisam-recover-options is deprecated and will be removed in a future release. Please use the full name instead.
150623  4:09:19 [Note] Plugin 'FEDERATED' is disabled.
150623  4:09:19 InnoDB: The InnoDB memory heap is disabled
150623  4:09:19 InnoDB: Mutexes and rw_locks use GCC atomic builtins
150623  4:09:19 InnoDB: Compressed tables use zlib 1.2.8
150623  4:09:19 InnoDB: Using Linux native AIO
150623  4:09:20 InnoDB: Initializing buffer pool, size = 128.0M
InnoDB: mmap(135987200 bytes) failed; errno 12
150623  4:09:20 InnoDB: Completed initialization of buffer pool
150623  4:09:20 InnoDB: Fatal error: cannot allocate memory for the buffer pool
150623  4:09:20 [ERROR] Plugin 'InnoDB' init function returned error.
150623  4:09:20 [ERROR] Plugin 'InnoDB' registration as a STORAGE ENGINE failed.
150623  4:09:20 [ERROR] Unknown/unsupported storage engine: InnoDB
150623  4:09:20 [ERROR] Aborting


150623  4:09:20 [Note] /usr/sbin/mysqld: Shutdown complete



```


```
$ free -m
                                  total       used       free     shared    buffers     cached
Mem:                           987        969         18         64         29        388
-/+ buffers/cache:        551        436
Swap:                          255         21        234
```




How can I prevent (I think) MySQL from crashing?


Many thanks

---

### Post by nerdtron on 2015-06-22
> "**Jun 23 04:09:18 www kernel: Out of memory: Kill process 2831 (mysqld) score 57 or sacrifice child** Jun 23 04:09:18 www kernel: Killed process 2831 (mysqld) total-vm:343084kB, anon-rss:25828kB, file-rss:0kB Jun 23 04:09:18 www kernel: init: mysql main process (2831) killed by KILL signal Jun 23 04:09:18 www kernel: init: mysql main process ended, respawning" 

How many transactions/queries are you expecting on the databases? It looks like the server rans out of memory. I think linode has a wiki page for optimizing mysql for low memory machines.

Mysql is memory hungry as it caches a lot on the RAM. I think increasing swap to about 1GB or more will help the server cope with database queries. But adding swap will not completely solve your problem. If your applications/transactions are growing, then you servers should also scale up.

---

### Post by pissedoffdude on 2015-06-22
Hi,

What are the specs of your mysql node?  I'm seeing that other users with a similar issue and they rectified it by increasing the swap space: [http://www.webtrafficexchange.com/solved-mysql-crash-fatal-error-cannot-allocate-memory-buffer-pool](http://www.webtrafficexchange.com/solved-mysql-crash-fatal-error-cannot-allocate-memory-buffer-pool)

I would also investigate the mysql connection pool.  How many total connections are there during the time frame of the outage:```
netstat -an | grep 3306
``` or whatever port you're using. You might want to lower the size of the connection pool if the node doesn't have the specs to support it.  Also, it might be a good idea to check the mysql transaction logs to see if there are any long standing queries, etc.  It would also be wise to monitor normal CPU/RAM usage during the timeframe of the outage and during normal periods.

---

### Post by rob134 on 2015-06-23
This is Longview, top one shows cpu usage. (timestamps of logs and longview are different)
Swap is 256mb now with 1gb of ram on the server. Not enough?

My situation is very similar to that [thread]("http://www.webtrafficexchange.com/solved-mysql-crash-fatal-error-cannot-allocate-memory-buffer-pool") since I'm running multiple wordpress websites as well.
I'll try reduce the [COLOR=white][FONT=andale mono]innodb_buffer_pool_size=64M [/FONT][/COLOR]first in my.cnf and see what happens :)

[IMG]http://www.seomandarin.com/wp-content/uploads/longview-mysql.jpg[/IMG]

---

### Post by pissedoffdude on 2015-06-23
Hmm, I'd say you should have at lest 2GBs of swap space considering those specs.  Get the result of the nestat during the outage.  It might be wise to limit the size of the connection pool.  It can be done via editing my cnf and adding
[mysqld]
max_connections = #

There's no one size fit's all answer for #, so see if you can retrieve the total number of connections via netstat.  You can do so with  ```
netstat -an | grep :3306 | wc -l

``` to get the count and maybe lower it by 5-15 in the my.cnf and restart mysqld.

---

### Post by SeijiSensei on 2015-06-23
That graph shows a lot of available disk cache before the crash, which Linux should have allocated to processes as needed.  It looks to me like you need to do some tuning to MySQL given the error message nerdtron highlighted.  [This document](https://dev.mysql.com/doc/refman/5.5/en/server-parameters.html) reports that the default setting for max-connections is 151.  Maybe you should set that to something like 50 for starters and see if it helps.

---

