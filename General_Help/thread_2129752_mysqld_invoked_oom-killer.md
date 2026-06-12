---
title: "mysqld invoked oom-killer"
date: 2013-03-27
forum: General Help
---

### Post by Wolfblitz on 2013-03-27
We have been having a bit of a problem on Ubuntu with the OOM manager killing MySQL.

The box is only a SQL server and does not share any of it's resources with other processes (ie. web server, etc.)

Here's what was printed to dmesg
```

[4379596.347992] mysqld invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0, oom_score_adj=0
[4379596.347996] mysqld cpuset=/ mems_allowed=0-1
[4379596.347998] Pid: 24310, comm: mysqld Not tainted 3.2.0-23-generic #36-Ubuntu
[4379596.348001] Call Trace:
[4379596.348011]  [<ffffffff810bfebd>] ? cpuset_print_task_mems_allowed+0x9d/0xb0
[4379596.348017]  [<ffffffff8111ac71>] dump_header+0x91/0xe0
[4379596.348019]  [<ffffffff8111aff5>] oom_kill_process+0x85/0xb0
[4379596.348021]  [<ffffffff8111b39a>] out_of_memory+0xfa/0x220
[4379596.348024]  [<ffffffff81120e1f>] __alloc_pages_nodemask+0x80f/0x820
[4379596.348029]  [<ffffffff811579c3>] alloc_pages_current+0xa3/0x110
[4379596.348031]  [<ffffffff8111783f>] __page_cache_alloc+0x8f/0xa0
[4379596.348034]  [<ffffffff81117cae>] ? find_get_page+0x1e/0x90
[4379596.348036]  [<ffffffff81119b54>] filemap_fault+0x234/0x3e0
[4379596.348041]  [<ffffffff8116de5b>] ? mem_cgroup_update_page_stat+0x2b/0x110
[4379596.348044]  [<ffffffff8113a0d2>] __do_fault+0x72/0x550
[4379596.348046]  [<ffffffff8113d71a>] handle_pte_fault+0xfa/0x200
[4379596.348049]  [<ffffffff81051ed2>] ? ttwu_queue+0x92/0xd0
[4379596.348051]  [<ffffffff8113dbd8>] handle_mm_fault+0x1f8/0x350
[4379596.348056]  [<ffffffff8165ffa0>] do_page_fault+0x150/0x520
[4379596.348060]  [<ffffffff810a0978>] ? do_futex+0xd8/0x1b0
[4379596.348065]  [<ffffffff812d9d04>] ? aa_net_perm+0x54/0x70
[4379596.348067]  [<ffffffff810a0b5a>] ? sys_futex+0x10a/0x1a0
[4379596.348069]  [<ffffffff8165cbf5>] page_fault+0x25/0x30
[4379596.348071] Mem-Info:
[4379596.348072] Node 0 Normal per-cpu:
[4379596.348074] CPU    0: hi:  186, btch:  31 usd:   1
[4379596.348075] CPU    1: hi:  186, btch:  31 usd:   0
[4379596.348076] CPU    2: hi:  186, btch:  31 usd:  17
[4379596.348078] CPU    3: hi:  186, btch:  31 usd:   0
[4379596.348079] CPU    4: hi:  186, btch:  31 usd:  58
[4379596.348080] CPU    5: hi:  186, btch:  31 usd:   0
[4379596.348082] CPU    6: hi:  186, btch:  31 usd:   9
[4379596.348083] CPU    7: hi:  186, btch:  31 usd:   0
[4379596.348084] CPU    8: hi:  186, btch:  31 usd:   2
[4379596.348086] CPU    9: hi:  186, btch:  31 usd:   0
[4379596.348087] CPU   10: hi:  186, btch:  31 usd:  30
[4379596.348088] CPU   11: hi:  186, btch:  31 usd:   0
[4379596.348089] CPU   12: hi:  186, btch:  31 usd:  59
[4379596.348091] CPU   13: hi:  186, btch:  31 usd:   0
[4379596.348092] CPU   14: hi:  186, btch:  31 usd:   0
[4379596.348093] CPU   15: hi:  186, btch:  31 usd:   0
[4379596.348094] Node 1 DMA per-cpu:
[4379596.348096] CPU    0: hi:    0, btch:   1 usd:   0
[4379596.348097] CPU    1: hi:    0, btch:   1 usd:   0
[4379596.348098] CPU    2: hi:    0, btch:   1 usd:   0
[4379596.348100] CPU    3: hi:    0, btch:   1 usd:   0
[4379596.348101] CPU    4: hi:    0, btch:   1 usd:   0
[4379596.348102] CPU    5: hi:    0, btch:   1 usd:   0
[4379596.348103] CPU    6: hi:    0, btch:   1 usd:   0
[4379596.348105] CPU    7: hi:    0, btch:   1 usd:   0
[4379596.348106] CPU    8: hi:    0, btch:   1 usd:   0
[4379596.348107] CPU    9: hi:    0, btch:   1 usd:   0
[4379596.348108] CPU   10: hi:    0, btch:   1 usd:   0
[4379596.348110] CPU   11: hi:    0, btch:   1 usd:   0
[4379596.348111] CPU   12: hi:    0, btch:   1 usd:   0
[4379596.348112] CPU   13: hi:    0, btch:   1 usd:   0
[4379596.348113] CPU   14: hi:    0, btch:   1 usd:   0
[4379596.348115] CPU   15: hi:    0, btch:   1 usd:   0
[4379596.348116] Node 1 DMA32 per-cpu:
[4379596.348117] CPU    0: hi:  186, btch:  31 usd:   2
[4379596.348118] CPU    1: hi:  186, btch:  31 usd:   0
[4379596.348120] CPU    2: hi:  186, btch:  31 usd:   0
[4379596.348121] CPU    3: hi:  186, btch:  31 usd:   3
[4379596.348122] CPU    4: hi:  186, btch:  31 usd:   0
[4379596.348124] CPU    5: hi:  186, btch:  31 usd:   0
[4379596.348125] CPU    6: hi:  186, btch:  31 usd:   0
[4379596.348126] CPU    7: hi:  186, btch:  31 usd:   0
[4379596.348127] CPU    8: hi:  186, btch:  31 usd:   0
[4379596.348129] CPU    9: hi:  186, btch:  31 usd:   0
[4379596.348130] CPU   10: hi:  186, btch:  31 usd:   0
[4379596.348131] CPU   11: hi:  186, btch:  31 usd:   0
[4379596.348132] CPU   12: hi:  186, btch:  31 usd:   0
[4379596.348134] CPU   13: hi:  186, btch:  31 usd:   0
[4379596.348135] CPU   14: hi:  186, btch:  31 usd:   0
[4379596.348136] CPU   15: hi:  186, btch:  31 usd:   0
[4379596.348137] Node 1 Normal per-cpu:
[4379596.348139] CPU    0: hi:  186, btch:  31 usd:   0
[4379596.348140] CPU    1: hi:  186, btch:  31 usd:  30
[4379596.348141] CPU    2: hi:  186, btch:  31 usd:   0
[4379596.348143] CPU    3: hi:  186, btch:  31 usd:  26
[4379596.348144] CPU    4: hi:  186, btch:  31 usd:   0
[4379596.348145] CPU    5: hi:  186, btch:  31 usd:  13
[4379596.348147] CPU    6: hi:  186, btch:  31 usd:   0
[4379596.348148] CPU    7: hi:  186, btch:  31 usd:  18
[4379596.348149] CPU    8: hi:  186, btch:  31 usd:   0
[4379596.348150] CPU    9: hi:  186, btch:  31 usd:   6
[4379596.348152] CPU   10: hi:  186, btch:  31 usd:   0
[4379596.348153] CPU   11: hi:  186, btch:  31 usd:   0
[4379596.348154] CPU   12: hi:  186, btch:  31 usd:   0
[4379596.348156] CPU   13: hi:  186, btch:  31 usd:   0
[4379596.348157] CPU   14: hi:  186, btch:  31 usd:   0
[4379596.348158] CPU   15: hi:  186, btch:  31 usd:   0
[4379596.348161] active_anon:7316682 inactive_anon:737085 isolated_anon:0
[4379596.348162]  active_file:0 inactive_file:76 isolated_file:0
[4379596.348162]  unevictable:0 dirty:0 writeback:131 unstable:0
[4379596.348163]  free:41161 slab_reclaimable:10827 slab_unreclaimable:16383
[4379596.348164]  mapped:0 shmem:4 pagetables:17914 bounce:0
[4379596.348166] Node 0 Normal free:47952kB min:45088kB low:56360kB high:67632kB active_anon:14938372kB inactive_anon:1245252kB active_file:0kB inactive_file:1000kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:16515072kB mlocked:0kB dirty:0kB writeback:96kB mapped:0kB shmem:8kB slab_reclaimable:19600kB slab_unreclaimable:36672kB kernel_stack:3072kB pagetables:32020kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:128 all_unreclaimable? yes
[4379596.348174] lowmem_reserve[]: 0 0 0 0
[4379596.348177] Node 1 DMA free:15892kB min:40kB low:48kB high:60kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15652kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:0kB slab_unreclaimable:16kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
[4379596.348186] lowmem_reserve[]: 0 3235 16087 16087
[4379596.348189] Node 1 DMA32 free:61836kB min:9044kB low:11304kB high:13564kB active_anon:2680376kB inactive_anon:538004kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:3313380kB mlocked:0kB dirty:0kB writeback:28kB mapped:4kB shmem:0kB slab_reclaimable:7152kB slab_unreclaimable:3868kB kernel_stack:504kB pagetables:7400kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:11 all_unreclaimable? yes
[4379596.348198] lowmem_reserve[]: 0 0 12852 12852
[4379596.348200] Node 1 Normal free:38964kB min:35928kB low:44908kB high:53892kB active_anon:11647980kB inactive_anon:1165084kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:13160448kB mlocked:0kB dirty:0kB writeback:400kB mapped:0kB shmem:8kB slab_reclaimable:16556kB slab_unreclaimable:24976kB kernel_stack:1872kB pagetables:32236kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:96 all_unreclaimable? yes
[4379596.348209] lowmem_reserve[]: 0 0 0 0
[4379596.348212] Node 0 Normal: 965*4kB 521*8kB 436*16kB 258*32kB 168*64kB 44*128kB 17*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 47580kB
[4379596.348220] Node 1 DMA: 1*4kB 0*8kB 1*16kB 0*32kB 2*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 3*4096kB = 15892kB
[4379596.348227] Node 1 DMA32: 671*4kB 358*8kB 363*16kB 255*32kB 169*64kB 97*128kB 47*256kB 6*512kB 0*1024kB 0*2048kB 1*4096kB = 61948kB
[4379596.348234] Node 1 Normal: 1599*4kB 683*8kB 428*16kB 267*32kB 90*64kB 15*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 1*4096kB = 39028kB
[4379596.348242] 16056 total pagecache pages
[4379596.348243] 15541 pages in swap cache
[4379596.348245] Swap cache stats: add 2998615, delete 2983074, find 3058697/3231766
[4379596.348246] Free swap  = 0kB
[4379596.348247] Total swap = 1952764kB
[4379596.424961] 8388592 pages RAM
[4379596.424965] 154844 pages reserved
[4379596.424966] 884 pages shared
[4379596.424966] 8191294 pages non-shared
[4379596.424968] [ pid ]   uid  tgid total_vm      rss cpu oom_adj oom_score_adj name
[4379596.424988] [  628]     0   628     4341       24   3       0             0 upstart-udev-br
[4379596.424992] [  631]     0   631     5527        1   1     -17         -1000 udevd
[4379596.424995] [ 1056]     0  1056     3797        1   9       0             0 upstart-socket-
[4379596.424999] [ 1081]     0  1081     4800       14   2       0             0 rpcbind
[4379596.425003] [ 1653]     0  1653     6385        0  12       0             0 rpc.idmapd
[4379596.425007] [ 1656]   101  1656    62561      527   3       0             0 rsyslogd
[4379596.425010] [ 1657]   107  1657     5376        1   1       0             0 rpc.statd
[4379596.425014] [ 1986]     0  1986     3946        2   3       0             0 getty
[4379596.425017] [ 1991]     0  1991     3946        2  11       0             0 getty
[4379596.425020] [ 1998]     0  1998     3742        0   2       0             0 xinetd
[4379596.425024] [ 2000]     0  2000     1082        1   0       0             0 acpid
[4379596.425027] [ 2001]     0  2001     4227        1   6       0             0 atd
[4379596.425030] [ 2002]     0  2002     4778       24   3       0             0 cron
[4379596.425033] [ 2022]     0  2022     3995       31   1       0             0 irqbalance
[4379596.425036] [ 2033]     0  2033    74461       29   2       0             0 automount
[4379596.425039] [ 2059]     0  2059    49082      649   2       0             0 fail2ban-server
[4379596.425043] [ 2062]     0  2062     5632       48   9       0             0 gam_server
[4379596.425046] [ 2079]     0  2079     3202        1  10       0             0 mcelog
[4379596.425051] [ 2143]     0  2143     6002        1  11       0             0 rpc.mountd
[4379596.425054] [ 2311]     0  2311     6277       31   1       0             0 master
[4379596.425057] [ 2343]     0  2343    18754       13   2       0             0 sensord
[4379596.425060] [ 2365]   110  2365    12181      103   3       0             0 snmpd
[4379596.425064] [ 2407]   103  2407    32083        2   0       0             0 whoopsie
[4379596.425067] [ 2921]   106  2921     6825       41   7       0             0 qmgr
[4379596.425070] [ 3252]     0  3252    12489       30   1     -17         -1000 sshd
[4379596.425073] [ 3354]   108  3354    10454       68   5       0             0 ntpd
[4379596.425076] [10892]     0 10892     3946        2   2       0             0 getty
[4379596.425079] [ 8841]     0  8841    20990       49   0       0             0 sshd
[4379596.425082] [ 9072]  1003  9072    22064       64  14       0             0 sshd
[4379596.425085] [ 9073]  1003  9073     3793       86   8       0             0 sftp-server
[4379596.425090] [26465]     0 26465     5526        0   4     -17         -1000 udevd
[4379596.425096] [26502]     0 26502     5394        3  14     -17         -1000 udevd
[4379596.425099] [27085]   112 27085 10766615  8033034   0       0             0 mysqld
[4379596.425102] [17659]     0 17659     3186       33   0       0             0 anacron
[4379596.425105] [17770]     0 17770     1100       25   0       0             0 sh
[4379596.425108] [17771]     0 17771     1075        4   4       0             0 run-parts
[4379596.425111] [19718]     0 19718     1100       26   6       0             0 mysqlbackup-dat
[4379596.425114] [21115]     0 21115     2370       64   0       0             0 mysqlbackup.sh
[4379596.425118] [22010]   106 22010     6793       70   2       0             0 pickup
[4379596.425120] [23531]     0 23531    24573      138   2       0             0 mysqldump
[4379596.425124] Out of memory: Kill process 27085 (mysqld) score 978 or sacrifice child
[4379596.426195] Killed process 27085 (mysqld) total-vm:43066460kB, anon-rss:32132136kB, file-rss:0kB

```

Ubuntu version
```

Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-23-generic x86_64)

```

uname -a
```

Linux xxxxxxxxxxx 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

tail -n26 /proc/cpuinfo
```

processor       : 15
vendor_id       : GenuineIntel
cpu family      : 6
model           : 44
model name      : Intel(R) Xeon(R) CPU           X5672  @ 3.20GHz
stepping        : 2
microcode       : 0x13
cpu MHz         : 1596.000
cache size      : 12288 KB
physical id     : 0
siblings        : 8
core id         : 10
cpu cores       : 4
apicid          : 21
initial apicid  : 21
fpu             : yes
fpu_exception   : yes
cpuid level     : 11
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid dca sse4_1 sse4_2 popcnt aes lahf_lm ida arat epb dts tpr_shadow vnmi flexpriority ept vpid
bogomips        : 6383.95
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management:

```

free -m
```

             total       used       free     shared    buffers     cached
Mem:         32163      29641       2522          0        157      12786
-/+ buffers/cache:      16697      15465
Swap:         1906         22       1884

```

mysql -V
```

mysql  Ver 14.14 Distrib 5.5.29, for debian-linux-gnu (x86_64) using readline 6.2

```

grep -vE "^$|^#" /etc/mysql/my.cnf
```

[client]
port            = 3306
socket          = /var/run/mysqld/mysqld.sock
[mysqld_safe]
socket          = /var/run/mysqld/mysqld.sock
nice            = 0
[mysqld]
user            = mysql
pid-file        = /var/run/mysqld/mysqld.pid
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
datadir         = /var/lib/mysql
tmpdir          = /var/tmp
lc-messages-dir = /usr/share/mysql
skip-external-locking
key_buffer              = 16M
max_allowed_packet      = 32M
thread_stack            = 192K
thread_cache_size       = 8
myisam-recover         = BACKUP
max_connections        = 600
query_cache_limit       = 1M
query_cache_size        = 16M
server-id               = 100
replicate_same_server_id = 0
report_host             = xxxxxxxxxxx
log_bin                 = bin.000000
log_bin_index           = bin.index
expire_logs_days        = 10
max_binlog_size         = 300M
master_info_file        = master.info
relay_log               = relay-bin.000000
relay_log_index         = relay-bin.index
relay_log_info_file     = relay-log.info
max_relay_log_size      = 300M
innodb_data_file_path           = ibdata1:30G:autoextend
innodb_autoextend_increment     = 64
innodb_buffer_pool_size         = 10240M
innodb_log_file_size            = 512M
innodb_log_buffer_size          = 16M
innodb_additional_mem_pool_size = 16M
federated
[mysqldump]
quick
quote-names
max_allowed_packet      = 16M
[mysql]
[isamchk]
key_buffer              = 16M
!includedir /etc/mysql/conf.d/

```

cat /etc/sysctl.d/60-vm.conf 
```

# Decrease swappiness for SQL from 60
vm.swappiness = 0

# Decrease RAM overcommit ratio from 50
# swap space + vm.overcommit_ratio % of RAM
vm.overcommit_ratio = 0

```

Any ideas?

---

