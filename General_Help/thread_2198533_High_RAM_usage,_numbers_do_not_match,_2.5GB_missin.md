---
title: "High RAM usage, numbers do not match, 2.5GB missing"
date: 2014-01-09
forum: General Help
---

### Post by oneone on 2014-01-09
Hi there,

I am running Xubuntu amd64 on a Lenovo T510 with 8GB of RAM. / is on a btrfs volume. After using the system for some days, the RAM usage (excluding cache) constantly grows and is not shrinking again when closing all applications or even logging out. I am aware of Linuxs caching mechanism, see [http://www.linuxatemyram.com]("http://www.linuxatemyram.com/"), this is not the problem here.

To show you what I mean, I logged out, shutdown lightdm, and saved the output of *free -m*, *cat /proc/meminfo* and *top* to file (see below). 
[I]
free[/I] reports a usage of 2.6GB. */proc/meminfo* tells us: 8GB total - 4.24GB free - 1.07GB cache = 2.69GB, which matches the output of *free*. 

The problem is, that the numbers do not match with those of *top*, which reports 131MB (sum of RES column, VIRT = 4.4GB).

[B]Who ate the remaining 2.5GB?
[/B]
Slab is about 82MB, so the kernel cache is not the bad guy.
Has it to do with btrfs? Does btrfs have an own cache, that is not included in these numbers?
I also used virtualbox, may this be the reason?

```

             total       used       free     shared    buffers     cached
Mem:          7845       3704       4141          0          0       1046
-/+ buffers/cache:       2657       5188
Swap:            0          0          0

MemTotal:        8033980 kB
MemFree:         4240468 kB
Buffers:             176 kB
Cached:          1071992 kB
SwapCached:            0 kB
Active:           408500 kB
Inactive:         751092 kB
Active(anon):      92064 kB
Inactive(anon):     1016 kB
Active(file):     316436 kB
Inactive(file):   750076 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:             0 kB
SwapFree:              0 kB
Dirty:                16 kB
Writeback:             0 kB
AnonPages:         87508 kB
Mapped:             9684 kB
Shmem:              5656 kB
Slab:              81652 kB
SReclaimable:      46388 kB
SUnreclaim:        35264 kB
KernelStack:        1688 kB
PageTables:         5208 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     4016988 kB
Committed_AS:     381508 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      287328 kB
VmallocChunk:   34359406280 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:     7041080 kB
DirectMap2M:     1204224 kB

top - 13:23:36 up 2 days, 19:05,  1 user,  load average: 0,00, 0,17, 0,52
Tasks: 184 total,   1 running, 183 sleeping,   0 stopped,   0 zombie
%Cpu(s): 17,1 us, 13,3 sy,  1,4 ni, 67,0 id,  0,6 wa,  0,0 hi,  0,6 si,  0,0 st
KiB Mem:   8033980 total,  3793652 used,  4240328 free,      176 buffers
KiB Swap:        0 total,        0 used,        0 free,  1071996 cached


  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND
 1167 whoopsie  20   0  448m  25m  940 S   0,0  0,3   0:03.18 whoopsie
28510 root      20   0 58952  16m  604 S   0,0  0,2   0:00.24 SystemToolsBack
  830 colord    20   0  305m  10m  316 S   0,0  0,1   0:00.44 colord
10611 al        20   0 25432 5324 1896 S   0,0  0,1   0:00.41 bash
10882 al        20   0 25432 3832  404 S   0,0  0,0   0:00.00 bash
 2472 root      20   0  432m 3804 1356 S   0,0  0,0   0:25.04 udisksd
  974 root      20   0  284m 3484 1264 S   0,0  0,0   0:00.72 polkitd
  945 root      20   0  264m 3220 1460 S   0,0  0,0   0:04.37 NetworkManager
 4773 root      20   0  145m 2800  676 S   0,0  0,0   0:00.21 cupsd
 1791 root      20   0 92392 2552 1836 S   0,0  0,0   0:00.02 login
 8836 root      20   0 10244 2444  136 S   0,0  0,0   0:00.01 dhclient
 1872 root      20   0  286m 2432 1360 S   0,0  0,0   0:03.17 accounts-daemon
 6926 root      20   0 10244 2432  132 S   0,0  0,0   0:00.00 dhclient
    1 root      20   0 27224 2380  740 S   0,0  0,0   0:02.23 init
  537 messageb  20   0 32024 2260  640 S   0,0  0,0   0:06.55 dbus-daemon
 2469 root      20   0  291m 2116  868 S   0,0  0,0   0:09.62 upowerd
 2002 root      20   0  104m 1452  500 S   0,0  0,0   0:00.13 winbindd
 7037 root      20   0 32444 1452  856 S   0,0  0,0   0:00.22 wpa_supplicant
  486 root      20   0 43032 1432  360 S   0,0  0,0   0:00.26 systemd-udevd
10885 al        20   0 21992 1424 1040 R   1,6  0,0   0:00.01 top
  597 root      20   0 19476 1404  844 S   0,0  0,0   0:00.16 bluetoothd
  536 syslog    20   0  241m 1376  348 S   0,0  0,0   0:11.12 rsyslogd
 1983 root      20   0  105m 1276  332 S   0,0  0,0   0:00.26 winbindd
  619 root      20   0 37168 1240  880 S   0,0  0,0   0:00.09 systemd-logind
  865 root      20   0 83484 1200  376 S   0,0  0,0   0:13.23 modem-manager
 1115 root      20   0 73072 1100  216 S   0,0  0,0   0:00.05 cups-browsed
15813 root      20   0  105m 1056  100 S   0,0  0,0   0:00.01 winbindd
15814 root      20   0  104m  952    0 S   0,0  0,0   0:00.00 winbindd
28507 root      20   0  207m  940  140 S   0,0  0,0   0:00.01 system-tools-ba
  480 root      20   0 17584  916  392 S   0,0  0,0   0:00.34 upstart-udev-br
  625 avahi     20   0 32464  856  376 S   0,0  0,0   0:00.89 avahi-daemon
 2430 rtkit     21   1  164m  744  492 S   0,0  0,0   0:01.66 rtkit-daemon
  998 root      20   0 15524  572   72 S   0,0  0,0   0:00.09 upstart-socket-
 1207 root      20   0 19160  496  272 S   0,0  0,0   0:13.94 irqbalance
 1121 root      20   0 25804  416  148 S   0,0  0,0   0:00.22 cron
 1824 nobody    20   0 32496  392  132 S   0,0  0,0   0:04.62 dnsmasq
  555 root      20   0 15272  324   96 S   0,0  0,0   0:00.14 upstart-file-br
 1122 root      20   0  4376  272  100 S   0,0  0,0   0:00.00 acpid
  634 avahi     20   0 32228  256    0 S   0,0  0,0   0:00.00 avahi-daemon
 2960 nobody    20   0 28184  256    0 S   0,0  0,0   0:00.07 dnsmasq
 1124 daemon    20   0 19124  172    0 S   0,0  0,0   0:00.00 atd
 1086 root      20   0 17320  168    0 S   0,0  0,0   0:00.00 getty
 1053 root      20   0 17320  160    0 S   0,0  0,0   0:00.00 getty
 1089 root      20   0 17320  160    0 S   0,0  0,0   0:00.00 getty
 1423 root      20   0  4360  160   44 S   0,0  0,0   2:24.40 hdapsd
 1067 root      20   0 17320  156    0 S   0,0  0,0   0:00.00 getty
 1083 root      20   0 17320  152    0 S   0,0  0,0   0:00.00 getty
 1533 root      20   0  4352  108    0 S   0,0  0,0   0:10.36 thinkfan
    2 root      20   0     0    0    0 S   0,0  0,0   0:00.24 kthreadd
    3 root      20   0     0    0    0 S   0,0  0,0   0:23.34 ksoftirqd/0
    5 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 kworker/0:0H
    7 root      rt   0     0    0    0 S   0,0  0,0   0:04.55 migration/0
    8 root      20   0     0    0    0 S   0,0  0,0   0:00.00 rcu_bh
    9 root      20   0     0    0    0 S   0,0  0,0   0:00.00 rcuob/0
   10 root      20   0     0    0    0 S   0,0  0,0   0:00.00 rcuob/1
   11 root      20   0     0    0    0 S   0,0  0,0   0:00.00 rcuob/2
   12 root      20   0     0    0    0 S   0,0  0,0   0:00.00 rcuob/3
   13 root      20   0     0    0    0 S   0,0  0,0   2:10.44 rcu_sched
   14 root      20   0     0    0    0 S   0,0  0,0   0:33.87 rcuos/0
   15 root      20   0     0    0    0 S   0,0  0,0   0:19.23 rcuos/1
   16 root      20   0     0    0    0 S   0,0  0,0   0:32.18 rcuos/2
   17 root      20   0     0    0    0 S   0,0  0,0   0:21.36 rcuos/3
   20 root      rt   0     0    0    0 S   0,0  0,0   0:02.67 migration/1
   21 root      20   0     0    0    0 S   0,0  0,0   0:01.87 ksoftirqd/1
   23 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 kworker/1:0H
   25 root      rt   0     0    0    0 S   0,0  0,0   0:02.12 migration/2
   26 root      20   0     0    0    0 S   0,0  0,0   0:02.94 ksoftirqd/2
   28 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 kworker/2:0H
   30 root      rt   0     0    0    0 S   0,0  0,0   0:02.31 migration/3
   31 root      20   0     0    0    0 S   0,0  0,0   0:01.88 ksoftirqd/3
   33 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 kworker/3:0H
   34 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 khelper
   35 root      20   0     0    0    0 S   0,0  0,0   0:00.01 kdevtmpfs
   36 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 netns
   37 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 writeback
   38 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 kintegrityd
   39 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 bioset
   41 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 kblockd
   42 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 ata_sff
   43 root      20   0     0    0    0 S   0,0  0,0   0:00.07 khubd
   44 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 md
   45 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 devfreq_wq
   49 root      20   0     0    0    0 S   0,0  0,0   0:00.17 khungtaskd
   50 root      20   0     0    0    0 S   0,0  0,0   2:12.95 kswapd0
   51 root      25   5     0    0    0 S   0,0  0,0   0:00.00 ksmd
   52 root      39  19     0    0    0 S   0,0  0,0   0:00.00 khugepaged
   53 root      20   0     0    0    0 S   0,0  0,0   0:00.02 fsnotify_mark
   54 root      20   0     0    0    0 S   0,0  0,0   0:00.00 ecryptfs-kthrea
   55 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 crypto
   67 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 kthrotld
   89 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 deferwq
   90 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 charger_manager
  138 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 firewire
  159 root      20   0     0    0    0 S   0,0  0,0   0:00.00 scsi_eh_0
  160 root      20   0     0    0    0 S   0,0  0,0   0:00.00 scsi_eh_1
  161 root      20   0     0    0    0 S   0,0  0,0   0:00.00 scsi_eh_2
  162 root      20   0     0    0    0 S   0,0  0,0   0:00.00 scsi_eh_3
  163 root      20   0     0    0    0 S   0,0  0,0   0:00.00 scsi_eh_4
  164 root      20   0     0    0    0 S   0,0  0,0   0:00.00 scsi_eh_5
  246 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 kdmflush
  247 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 bioset
  248 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 kcryptd_io
  249 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 kcryptd
  250 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 bioset
  261 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 bioset
  272 root      20   0     0    0    0 S   0,0  0,0   0:00.10 btrfs-genwork-1
  273 root      20   0     0    0    0 S   0,0  0,0   0:02.99 btrfs-submit-1
  275 root      20   0     0    0    0 S   0,0  0,0   0:00.02 btrfs-fixup-1
  278 root      20   0     0    0    0 S   0,0  0,0   0:00.02 btrfs-rmw-1
  279 root      20   0     0    0    0 S   0,0  0,0   0:00.02 btrfs-endio-rai
  280 root      20   0     0    0    0 S   0,0  0,0   0:00.02 btrfs-endio-met
  282 root      20   0     0    0    0 S   0,0  0,0   0:01.30 btrfs-freespace
  283 root      20   0     0    0    0 S   0,0  0,0   0:01.63 btrfs-delayed-m
  284 root      20   0     0    0    0 S   0,0  0,0   0:00.03 btrfs-cache-1
  285 root      20   0     0    0    0 S   0,0  0,0   0:00.02 btrfs-readahead
  287 root      20   0     0    0    0 S   0,0  0,0   0:00.02 btrfs-qgroup-re
  292 root      20   0     0    0    0 S   0,0  0,0   0:26.02 btrfs-cleaner
  293 root      20   0     0    0    0 S   0,0  0,0   2:08.76 btrfs-transacti
  459 root      20   0     0    0    0 S   0,0  0,0   0:00.00 jbd2/sda3-8
  460 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 ext4-rsv-conver
  461 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 ext4-unrsv-conv
  600 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 ktpacpid
  605 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 cfg80211
  627 root      20   0     0    0    0 S   0,0  0,0   0:01.07 ips-adjust
  629 root      20   0     0    0    0 S   0,0  0,0   0:25.55 ips-monitor
  635 root      10 -10     0    0    0 S   0,0  0,0   0:00.00 krfcommd
  642 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 kpsmoused
  651 root     -51   0     0    0    0 S   0,0  0,0   0:05.29 irq/44-iwlwifi
  684 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 hd-audio0
  698 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 hd-audio1
  780 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 kvm-irqfd-clean
  796 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 iwlwifi
 1426 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 hci0
 1427 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 hci0
 1562 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 iprt
 1900 root      20   0     0    0    0 S   0,0  0,0   0:00.00 kauditd
 3507 root     -51   0     0    0    0 S   0,0  0,0   0:00.00 irq/41-mei_me
 5235 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 kdmflush
 5237 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 bioset
 5238 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 kcryptd_io
 5239 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 kcryptd
 5240 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 bioset
 5250 root      20   0     0    0    0 S   0,0  0,0   0:00.03 btrfs-genwork-1
 5251 root      20   0     0    0    0 S   0,0  0,0   0:00.11 btrfs-submit-1
 5252 root      20   0     0    0    0 S   0,0  0,0   0:00.02 btrfs-delalloc-
 5253 root      20   0     0    0    0 S   0,0  0,0   0:00.02 btrfs-fixup-1
 5254 root      20   0     0    0    0 S   0,0  0,0   0:02.30 btrfs-endio-1
 5256 root      20   0     0    0    0 S   0,0  0,0   0:00.02 btrfs-rmw-1
 5257 root      20   0     0    0    0 S   0,0  0,0   0:00.02 btrfs-endio-rai
 5258 root      20   0     0    0    0 S   0,0  0,0   0:00.03 btrfs-endio-met
 5260 root      20   0     0    0    0 S   0,0  0,0   0:00.04 btrfs-freespace
 5261 root      20   0     0    0    0 S   0,0  0,0   0:00.07 btrfs-delayed-m
 5262 root      20   0     0    0    0 S   0,0  0,0   0:00.03 btrfs-cache-1
 5263 root      20   0     0    0    0 S   0,0  0,0   0:00.02 btrfs-readahead
 5265 root      20   0     0    0    0 S   0,0  0,0   0:00.02 btrfs-qgroup-re
 5267 root      20   0     0    0    0 S   0,0  0,0   0:00.14 btrfs-cleaner
 5268 root      20   0     0    0    0 S   0,0  0,0   0:00.39 btrfs-transacti
 5895 root      20   0     0    0    0 S   0,0  0,0   0:00.12 btrfs-endio-met
 6781 root      20   0     0    0    0 S   0,0  0,0   0:01.69 btrfs-worker-2
 6785 root      20   0     0    0    0 S   0,0  0,0   0:00.06 btrfs-endio-wri
 6840 root      20   0     0    0    0 S   0,0  0,0   0:00.01 btrfs-flush_del
 7183 root       0 -20     0    0    0 S   0,0  0,0   0:00.42 kworker/u9:1
 7482 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 kworker/1:1H
 7483 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 kworker/2:1H
 7484 root       0 -20     0    0    0 S   0,0  0,0   0:00.00 kworker/3:1H
 9364 root       0 -20     0    0    0 S   0,0  0,0   0:00.17 kworker/u9:2
 9609 root      20   0     0    0    0 S   0,0  0,0   0:00.09 btrfs-worker-2
 9635 root      20   0     0    0    0 S   0,0  0,0   0:00.40 kworker/u8:2
 9990 root      20   0     0    0    0 S   0,0  0,0   0:00.78 kworker/3:0
 9998 root      20   0     0    0    0 S   0,0  0,0   0:01.33 kworker/2:0
 9999 root      20   0     0    0    0 S   0,0  0,0   0:01.47 kworker/0:2
10000 root      20   0     0    0    0 S   0,0  0,0   0:00.25 kworker/1:1
10009 root      20   0     0    0    0 S   0,0  0,0   0:00.28 kworker/u8:3
10068 root      20   0     0    0    0 S   0,0  0,0   0:00.13 btrfs-endio-met
10089 root      20   0     0    0    0 S   0,0  0,0   0:00.18 btrfs-endio-6
10222 root      20   0     0    0    0 S   0,0  0,0   0:00.02 btrfs-delalloc-
10246 root      20   0     0    0    0 S   0,0  0,0   0:00.02 btrfs-endio-wri
10385 root      20   0     0    0    0 S   0,0  0,0   0:00.40 kworker/2:2
10421 root      20   0     0    0    0 S   0,0  0,0   0:00.04 kworker/0:1
10453 root      20   0     0    0    0 S   0,0  0,0   0:00.00 kworker/1:0
10458 root      20   0     0    0    0 S   0,0  0,0   0:00.09 kworker/3:1
10471 root      20   0     0    0    0 S   0,0  0,0   0:00.07 kworker/u8:1
10879 root      20   0     0    0    0 S   0,0  0,0   0:00.00 kworker/3:2
31295 root      20   0     0    0    0 S   0,0  0,0   0:00.00 btrfs-flush_del

```

---

### Post by oneone on 2014-01-09
concerning btrfs: If I run [baobab]("https://help.ubuntu.com/community/Baobab") on / and watch */proc/meminfo*, then I see, that reclaimable Slab grows huge. Slab is counted as used memory in the output of *free*, but the reclaimable Slab is released as memory pressure grows. 

So, the btrfs cache memory is reported as used, because it's in Slab, but effectively behaves like memory used for the cache.

---

### Post by oneone on 2014-01-12
[COLOR=#000000]interesting in this context[/COLOR]

[https://github.com/pixelb/ps_mem/tree/master](https://github.com/pixelb/ps_mem/tree/master)

---

### Post by devine.steve on 2014-01-12
Myself I prefer top.

---

### Post by oneone on 2014-01-29
What has this to do with the actual question?

---

### Post by oneone on 2014-01-29
Just as a note: The system is now running for 13 days without this problem to occur.
I suspect VirtualBox to be eating the memory (after crash?). I did not use VirtualBox in these 13 days, but I did in the initial question. The memory assigned to the host was 2GB. Maybe this is it, maybe not.

---

### Post by tgalati4 on 2014-01-30
So you had a Virtual Box running with 2GB set aside for it and it was running an operating system which presumably crashed and you are wondering why you are missing 2.5GB of RAM?  I would be more interested in why the virtual machine crashed.  If this virtual machine operating system is what I think it is, then how is that a linux problem?

---

### Post by oneone on 2014-01-30
Hi tgalati4,

First, I am not 100% sure if the VirtualBox crashed in the setup I described, but if I remember it correctly it did.

Second, by "VirtualBox crashed" I mean that the virtual machine, the emulator, crashed, not the OS running inside the VM. A crash of the OS inside the VM should not affect the VM itself.

---

### Post by tgalati4 on 2014-01-30
Fair enough.  Let us know if it acts up again and it is repeatable, then you may have found a bug with your combination of hardware and software.

---

### Post by Psyker7 on 2014-02-16
Strangely this is the only place I've seen someone encountering similar issues, with VM's running on top of BTRFS, despite scouring BTRFS mailing lists.

Virtual box or qemu both seem to cause my free -m usage to not match the sum of my ps output, getting progressively worse the longer the VM stays open. Unfortunately it happens slowly, so it only becomes an issue after 3/4+ hours of the VM being open, meaning it took ages to actually track down.
It wouldn't be a huge issue, except it means I have to reboot my desktop occasionally now, rather than leave it running for weeks on end :(

---

