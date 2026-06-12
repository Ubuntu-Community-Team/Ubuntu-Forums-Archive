---
title: "ZFS stuck after destroying deduped fs"
date: 2012-12-02
forum: General Help
---

### Post by Zfs on 2012-12-02
Help???

I have a Ubuntu 12.04 server with 32 GB RAM and two 8-disk ubuntu-zfs pools.  One had dedup on and one had it off.  Both pools had about 9 TB data loaded. The one with dedup on took 18 hours to scrub, the one without dedup took 7 hours. I also had a cron job creating snapshots of both pools, averaging about 5 snapshots per filesystem.

Yesterday the deduped pool scrub slowed to a crawl and I decided to get rid of the dedup table - I only gained about 500GB space on 9 TB of data.  zpool status -D showed that the dedup table had 80 million entries! 

So I did the following.
- stopped the scrub, disabled dedup using zfs set dedup=off.
- moved critical data off the deduped pool, using zfs send|zfs receive. This ran at about 350Mbyte/second.
- when this filesystem was copied to the non-deduped pool, I issued the command zfs destroy -r [pool/filesystem], to get rid of all the snapshots too.
- after that any zfs command just hung. zfs list - hung. htop showed that txg_sync was active, but only about 2% CPU. atop showed all the disks in the dedup array still reading - no writes. 
- I left it for about an hour.  System working fine, but any zfs or zpool command just hung.
- I decided to reboot the system to see if zfs would come back.  Reboot hung.  I had to do a hard shutdown and reboot.
- The system came back but all zfs commands still hung.  Due to some megaraid issue, the disks always attached late and I had to issue 'zfs mount -a' to get the zfs array up.  This used to be reliable, but it doesn't work anymore since any zfs command just hangs. atop showed the pool disks reading a lot - more about that later.
- dmesg states zpool:4309 blocked for more than 120 seconds.
- What can I do to get my zfs back? Any zfs or zpool command just hangs?

top:
```
top - 19:47:07 up 11:10,  4 users,  load average: 17.06, 16.63, 13.75
Tasks: 271 total,   4 running, 267 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  1.9%sy,  0.0%ni, 98.1%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:  32910512k total, 14760496k used, 18150016k free,   115368k buffers
Swap: 33521660k total,        0k used, 33521660k free,   330788k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 3837 root      20   0 25560  996  784 D    4  0.0   5:46.83 zfs
 3938 root      39  19     0    0    0 R    2  0.0   3:14.65 z_rd_int/1
 3939 root      39  19     0    0    0 S    2  0.0   3:15.27 z_rd_int/2
 3940 root      39  19     0    0    0 S    2  0.0   3:15.95 z_rd_int/3
 3942 root      39  19     0    0    0 S    2  0.0   3:23.06 z_rd_int/5
 3943 root      39  19     0    0    0 S    2  0.0   3:23.32 z_rd_int/6
 3944 root      39  19     0    0    0 R    2  0.0   3:22.54 z_rd_int/7
 3941 root      39  19     0    0    0 S    1  0.0   2:24.68 z_rd_int/4
 3937 root      39  19     0    0    0 S    1  0.0   2:12.42 z_rd_int/0
10373 root      20   0     0    0    0 S    1  0.0   0:00.42 kworker/6:0
 3981 root      39  19     0    0    0 D    0  0.0   1:18.66 z_fr_iss/2
 3982 root      39  19     0    0    0 D    0  0.0   1:19.43 z_fr_iss/3
 3983 root      39  19     0    0    0 D    0  0.0   1:17.80 z_fr_iss/4
 5223 root      20   0     0    0    0 S    0  0.0   0:20.36 kworker/0:1
 5962 root      20   0     0    0    0 R    0  0.0   0:14.56 kworker/1:0
10372 root      20   0     0    0    0 S    0  0.0   0:01.00 kworker/0:2
10764 root      20   0 17476 1428  944 R    0  0.0   0:00.10 top

```

htop shows that the zfs thread taking 4% CPU time (and 5 CPU hours up now) to is the command zfs list - that I issued before the reboot!

atop shows that 8 hard disks are at 100% busy:
```
PRC | sys    2.32s  | user   0.01s  | #proc    271  | #tslpu    17 |  #zombie    0 |  #exit      0 |
CPU | sys      18%  | user      0%  | irq       0%  | idle    782% |  wait      0% |  avgscal  34% |
cpu | sys       3%  | user      0%  | irq       0%  | idle     97% |  cpu000 w  0% |  avgscal  34% |
cpu | sys       4%  | user      0%  | irq       0%  | idle     96% |  cpu002 w  0% |  avgscal  33% |
cpu | sys       3%  | user      0%  | irq       0%  | idle     97% |  cpu001 w  0% |  avgscal  34% |
cpu | sys       3%  | user      0%  | irq       0%  | idle     97% |  cpu003 w  0% |  avgscal  37% |
cpu | sys       2%  | user      0%  | irq       0%  | idle     98% |  cpu007 w  0% |  avgscal  33% |
cpu | sys       1%  | user      0%  | irq       0%  | idle     99% |  cpu005 w  0% |  avgscal  33% |
cpu | sys       1%  | user      0%  | irq       0%  | idle     99% |  cpu006 w  0% |  avgscal  33% |
cpu | sys       1%  | user      0%  | irq       0%  | idle     99% |  cpu004 w  0% |  avgscal  33% |
CPL | avg1   17.11  | avg5   16.95  | avg15  14.68  | csw    37633 |  intr   31811 |  numcpu     8 |
MEM | tot    31.4G  | free   17.3G  | cache 323.1M  | dirty   0.0M |  buff  112.7M |  slab  716.0M |
SWP | tot    32.0G  | free   32.0G  |               |              |  vmcom 634.9M |  vmlim  47.7G |
LVM |  galaxy-root  | busy      0%  | read       0  | write      5 |  MBw/s   0.00 |  avio 0.00 ms |
DSK |          sdf  | busy    101%  | read    2031  | write      0 |  MBw/s   0.00 |  avio 4.92 ms |
DSK |          sde  | busy     99%  | read    1996  | write      0 |  MBw/s   0.00 |  avio 4.93 ms |
DSK |          sdh  | busy     98%  | read    2019  | write      0 |  MBw/s   0.00 |  avio 4.84 ms |
DSK |          sdg  | busy     98%  | read    1968  | write      0 |  MBw/s   0.00 |  avio 4.97 ms |
DSK |          sdj  | busy     97%  | read    1989  | write      0 |  MBw/s   0.00 |  avio 4.87 ms |
DSK |          sdi  | busy     97%  | read    1956  | write      0 |  MBw/s   0.00 |  avio 4.93 ms |
DSK |          sdd  | busy     96%  | read    1927  | write      0 |  MBw/s   0.00 |  avio 4.97 ms |
DSK |          sdc  | busy     95%  | read    1923  | write      0 |  MBw/s   0.00 |  avio 4.92 ms |
DSK |          sda  | busy      0%  | read       0  | write      4 |  MBw/s   0.00 |  avio 0.00 ms |
NET | transport     | tcpi       6  | tcpo       7  | udpi      20 |  udpo       0 |  tcpao      0 |
NET | network       | ipi       34  | ipo        6  | ipfrw      0 |  deliv     34 |  icmpo      0 |
NET | eth0      0%  | pcki      76  | pcko       9  | si    7 Kbps |  so    4 Kbps |  erro       0 |

  PID RUID      THR  SYSCPU  USRCPU  VGROW  RGROW  RDDSK   WRDSK ST EXC S CPUNR  CPU CMD         1/3
 3837 root        1   0.60s   0.00s     0K     0K   168K      0K --   - D     0   6% zfs
 3939 root        1   0.20s   0.00s     0K     0K  8188K      0K --   - S     2   2% z_rd_int/2
 3942 root        1   0.20s   0.00s     0K     0K  8436K      0K --   - S     5   2% z_rd_int/5
 3943 root        1   0.20s   0.00s     0K     0K  8256K      0K --   - S     6   2% z_rd_int/6
 3938 root        1   0.19s   0.00s     0K     0K  8196K      0K --   - R     1   2% z_rd_int/1
 3940 root        1   0.19s   0.00s     0K     0K  8068K      0K --   - S     3   2% z_rd_int/3
 3944 root        1   0.19s   0.00s     0K     0K  8404K      0K --   - S     7   2% z_rd_int/7
 3941 root        1   0.11s   0.00s     0K     0K  8520K      0K --   - S     4   1% z_rd_int/4
 3937 root        1   0.10s   0.00s     0K     0K  8244K      0K --   - S     0   1% z_rd_int/0
 3922 root        1   0.08s   0.00s     0K     0K     0K      0K --   - S     3   1% kworker/3:4
 5095 root        1   0.05s   0.00s     0K     0K     0K      0K --   - R     1   1% kworker/1:4
10796 root        1   0.05s   0.00s     0K     0K     0K      0K --   - S     2   1% kworker/2:2

```

This means that the array is busy.  zfs is working, but it does not allow me to issue any commands, or mount the pools.  Some dmesg errors:
```
[  840.980093] INFO: task modprobe:239 blocked for more than 120 seconds.
[  840.980114] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  840.980126] modprobe        D ffffffff81806200     0   239    154 0x00000004
[  840.980134]  ffff880806ae5b48 0000000000000086 ffff880806ae5ae8 ffffffff8101adf3
[  840.980142]  ffff880806ae5fd8 ffff880806ae5fd8 ffff880806ae5fd8 0000000000013780
[  840.980149]  ffff88080be99700 ffff880806afae00 ffff880806ae5b58 ffff88080bfad840
[  840.980155] Call Trace:
[  840.980167]  [<ffffffff8101adf3>] ? native_sched_clock+0x13/0x80
[  840.980176]  [<ffffffff816579cf>] schedule+0x3f/0x60
[  840.980196]  [<ffffffffa00093f5>] megasas_issue_blocked_cmd+0x75/0xb0 [megaraid_sas]
[  840.980203]  [<ffffffff8108aa50>] ? add_wait_queue+0x60/0x60
[  840.980213]  [<ffffffffa000a6c9>] megasas_get_seq_num+0xd9/0x260 [megaraid_sas]
[  840.980222]  [<ffffffffa000ab31>] megasas_start_aen+0x31/0x60 [megaraid_sas]
[  840.980233]  [<ffffffffa00136f1>] megasas_probe_one+0x69a/0x81c [megaraid_sas]
[  840.980240]  [<ffffffff813345bc>] local_pci_probe+0x5c/0xd0
[  840.980247]  [<ffffffff81335e89>] __pci_device_probe+0xf9/0x100
[  840.980255]  [<ffffffff8130ce6a>] ? kobject_get+0x1a/0x30
[  840.980263]  [<ffffffff81335eca>] pci_device_probe+0x3a/0x60
[  840.980270]  [<ffffffff813f5278>] really_probe+0x68/0x190
[  840.980275]  [<ffffffff813f5505>] driver_probe_device+0x45/0x70
[  840.980280]  [<ffffffff813f55db>] __driver_attach+0xab/0xb0
[  840.980285]  [<ffffffff813f5530>] ? driver_probe_device+0x70/0x70
[  840.980290]  [<ffffffff813f5530>] ? driver_probe_device+0x70/0x70
[  840.980295]  [<ffffffff813f436c>] bus_for_each_dev+0x5c/0x90
[  840.980301]  [<ffffffff813f503e>] driver_attach+0x1e/0x20
[  840.980305]  [<ffffffff813f4c90>] bus_add_driver+0x1a0/0x270
[  840.980312]  [<ffffffffa001e000>] ? 0xffffffffa001dfff
[  840.980317]  [<ffffffff813f5b46>] driver_register+0x76/0x140
[  840.980323]  [<ffffffffa001e000>] ? 0xffffffffa001dfff
[  840.980328]  [<ffffffff81335b66>] __pci_register_driver+0x56/0xd0
[  840.980333]  [<ffffffffa001e000>] ? 0xffffffffa001dfff
[  840.980343]  [<ffffffffa001e09e>] megasas_init+0x9e/0x1000 [megaraid_sas]
[  840.980350]  [<ffffffff81002040>] do_one_initcall+0x40/0x180
[  840.980358]  [<ffffffff810a82fe>] sys_init_module+0xbe/0x230
[  840.980364]  [<ffffffff81661ec2>] system_call_fastpath+0x16/0x1b

[  840.980398] INFO: task zpool:4309 blocked for more than 120 seconds.
[  840.980408] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  840.980419] zpool           D ffffffff81806200     0  4309   4251 0x00000000
[  840.980425]  ffff880769c53d98 0000000000000086 0000000000000000 0000000000000000
[  840.980432]  ffff880769c53fd8 ffff880769c53fd8 ffff880769c53fd8 0000000000013780
[  840.980438]  ffffffff81c0d020 ffff8807d478c500 0000002781162c60 ffffffffa0230dc0
[  840.980445] Call Trace:
[  840.980453]  [<ffffffff816579cf>] schedule+0x3f/0x60
[  840.980460]  [<ffffffff816587d7>] __mutex_lock_slowpath+0xd7/0x150
[  840.980471]  [<ffffffffa00edb58>] ? nv_alloc_nosleep_spl+0x28/0x30 [znvpair]
[  840.980485]  [<ffffffff816583ea>] mutex_lock+0x2a/0x50
[  840.980549]  [<ffffffffa01abfa2>] spa_all_configs+0x52/0x120 [zfs]
[  840.980611]  [<ffffffffa01d5594>] zfs_ioc_pool_configs+0x24/0x60 [zfs]
[  840.980664]  [<ffffffffa01da25c>] zfsdev_ioctl+0xdc/0x1b0 [zfs]
[  840.980672]  [<ffffffff81189c5a>] do_vfs_ioctl+0x8a/0x340
[  840.980678]  [<ffffffff81142793>] ? do_munmap+0x1f3/0x2f0
[  840.980683]  [<ffffffff81189fa1>] sys_ioctl+0x91/0xa0
[  840.980688]  [<ffffffff81661ec2>] system_call_fastpath+0x16/0x1b

```

---

