---
title: "VM Freeze, possible disk IO problem"
date: 2014-08-01
forum: General Help
---

### Post by Rob_Donovan on 2014-08-01
Hi,

I'm running Ubuntu 12.04 LTS with all the updates applied:

3.2.0-67-virtual #101-Ubuntu SMP Tue Jul 15 17:58:37 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

I'm using MS Azure to host my VM.

24 hours ago, my machine started to 'freeze' and have awful performance problems. (I'm running apache2.2, php5, mysql... running 4 very small web sites, with little traffic)

I've now found that it looks like it something to do with the disk IO.

I'm quite computer 'literate', so I've done alot of investigation already to rule out things, DDOS attack, rogue running processes etc.

I've noticed I get lots of these messages in /var/log/syslog when its having problems:

```
Aug  1 07:46:06 localhost kernel: [ 2873.633314] hv_storvsc vmbus_0_1: cmd 0x2a scsi status 0x2 srb status 0x4
Aug  1 07:46:06 localhost kernel: [ 2873.633329] hv_storvsc vmbus_0_1: cmd 0x2a scsi status 0x2 srb status 0x4
Aug  1 07:46:06 localhost kernel: [ 2873.633334] hv_storvsc vmbus_0_1: cmd 0x2a scsi status 0x2 srb status 0x4
Aug  1 07:46:06 localhost kernel: [ 2873.633338] hv_storvsc vmbus_0_1: cmd 0x2a scsi status 0x2 srb status 0x4
Aug  1 07:46:06 localhost kernel: [ 2873.633342] hv_storvsc vmbus_0_1: cmd 0x2a scsi status 0x2 srb status 0x4
Aug  1 07:46:06 localhost kernel: [ 2873.633345] hv_storvsc vmbus_0_1: cmd 0x2a scsi status 0x2 srb status 0x4
Aug  1 07:46:06 localhost kernel: [ 2873.633349] hv_storvsc vmbus_0_1: cmd 0x2a scsi status 0x2 srb status 0x4
Aug  1 07:46:06 localhost kernel: [ 2873.633352] hv_storvsc vmbus_0_1: cmd 0x2a scsi status 0x2 srb status 0x4
Aug  1 07:46:06 localhost kernel: [ 2873.633355] hv_storvsc vmbus_0_1: cmd 0x2a scsi status 0x2 srb status 0x4
Aug  1 07:46:06 localhost kernel: [ 2873.633359] hv_storvsc vmbus_0_1: cmd 0x2a scsi status 0x2 srb status 0x4
Aug  1 07:46:06 localhost kernel: [ 2873.633362] hv_storvsc vmbus_0_1: cmd 0x2a scsi status 0x2 srb status 0x4
Aug  1 07:46:06 localhost kernel: [ 2873.633366] hv_storvsc vmbus_0_1: cmd 0x2a scsi status 0x2 srb status 0x4
Aug  1 07:46:06 localhost kernel: [ 2873.633370] hv_storvsc vmbus_0_1: cmd 0x2a scsi status 0x2 srb status 0x4
Aug  1 07:46:06 localhost kernel: [ 2873.633373] hv_storvsc vmbus_0_1: cmd 0x2a scsi status 0x2 srb status 0x4
Aug  1 07:46:06 localhost kernel: [ 2873.633377] hv_storvsc vmbus_0_1: cmd 0x2a scsi status 0x2 srb status 0x4
Aug  1 07:46:06 localhost kernel: [ 2873.633380] hv_storvsc vmbus_0_1: cmd 0x2a scsi status 0x2 srb status 0x4
Aug  1 07:46:06 localhost kernel: [ 2873.633383] hv_storvsc vmbus_0_1: cmd 0x2a scsi status 0x2 srb status 0x4
Aug  1 07:46:06 localhost kernel: [ 2876.680536] hv_storvsc vmbus_0_1: cmd 0x2a scsi status 0x2 srb status 0x4
Aug  1 07:47:29 localhost kernel: [ 2969.722676] INFO: task jbd2/sda1-8:236 blocked for more than 120 seconds.
Aug  1 07:47:29 localhost kernel: [ 2969.725433] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Aug  1 07:47:29 localhost kernel: [ 2969.728180] jbd2/sda1-8     D 0000000000000000     0   236      2 0x00000000
Aug  1 07:47:29 localhost kernel: [ 2969.728186]  ffff880109ec9ce0 0000000000000046 ffff880109ec9cb0 0000000300000001
Aug  1 07:47:29 localhost kernel: [ 2969.728190]  ffff880109ec9fd8 ffff880109ec9fd8 ffff880109ec9fd8 0000000000013700
Aug  1 07:47:29 localhost kernel: [ 2969.728194]  ffff880109dc16f0 ffff880109b5c4d0 ffff880109ec9cf0 ffff880109ec9df8
Aug  1 07:47:29 localhost kernel: [ 2969.728198] Call Trace:
Aug  1 07:47:29 localhost kernel: [ 2969.728207]  [<ffffffff8165b5df>] schedule+0x3f/0x60
Aug  1 07:47:29 localhost kernel: [ 2969.728212]  [<ffffffff8126226c>] jbd2_journal_commit_transaction+0x18c/0x1270
Aug  1 07:47:29 localhost kernel: [ 2969.728217]  [<ffffffff8165d6ee>] ? _raw_spin_lock_irqsave+0x2e/0x40
Aug  1 07:47:29 localhost kernel: [ 2969.728222]  [<ffffffff81077da8>] ? lock_timer_base.isra.29+0x38/0x70
Aug  1 07:47:29 localhost kernel: [ 2969.728226]  [<ffffffff8108b830>] ? add_wait_queue+0x60/0x60
Aug  1 07:47:29 localhost kernel: [ 2969.728230]  [<ffffffff81266fdb>] kjournald2+0xbb/0x220
Aug  1 07:47:29 localhost kernel: [ 2969.728233]  [<ffffffff8108b830>] ? add_wait_queue+0x60/0x60
Aug  1 07:47:29 localhost kernel: [ 2969.728236]  [<ffffffff81266f20>] ? commit_timeout+0x10/0x10
Aug  1 07:47:29 localhost kernel: [ 2969.728239]  [<ffffffff8108ad8c>] kthread+0x8c/0xa0
Aug  1 07:47:29 localhost kernel: [ 2969.728243]  [<ffffffff81667bf4>] kernel_thread_helper+0x4/0x10
Aug  1 07:47:29 localhost kernel: [ 2969.728246]  [<ffffffff8108ad00>] ? flush_kthread_worker+0xa0/0xa0
Aug  1 07:47:29 localhost kernel: [ 2969.728249]  [<ffffffff81667bf0>] ? gs_change+0x13/0x13

```

sar -d is also reporting massive await times on the disk:

```
07:05:01 AM       DEV       tps  rd_sec/s  wr_sec/s  avgrq-sz  avgqu-sz     await     svctm     %util
07:15:01 AM    dev8-0      4.33    105.39     17.74     28.42      0.11     26.44     21.67      9.39
07:15:01 AM   dev8-16      0.40      0.86      2.84      9.24      0.00      4.20      0.97      0.04
07:25:02 AM    dev8-0      8.51    565.68     18.77     68.71      0.07      8.41      4.47      3.80
07:25:02 AM   dev8-16      2.11      2.01     39.68     19.80      0.02      8.18      0.53      0.11
07:35:01 AM    dev8-0      2.60     86.33     10.63     37.26      0.02      8.02      5.57      1.45
07:35:01 AM   dev8-16      0.19      1.51      0.00      8.00      0.00     11.54      1.68      0.03
07:47:48 AM    dev8-0      1.42     24.90     10.20     24.75      7.55   5322.78    462.15     65.53
07:47:48 AM   dev8-16      1.09      8.03      1.24      8.51      0.00      3.98      0.60      0.07
07:55:02 AM    dev8-0      2.34     36.63     14.39     21.82      2.25    961.63    174.50     40.80
07:55:02 AM   dev8-16      0.07      0.58      0.00      8.00      0.00     14.19      1.94      0.01
08:05:47 AM    dev8-0      0.77     10.32      6.91     22.32     14.46  18721.94   1138.97     87.95
08:05:47 AM   dev8-16      0.02      0.20      0.00      8.00      0.00      9.75      1.25      0.00
08:15:01 AM    dev8-0      3.25     65.30      9.89     23.12     10.44   2165.47    231.99     75.44
08:15:01 AM   dev8-16      0.32      1.51      1.31      8.92      0.00      7.26      0.74      0.02
08:25:01 AM    dev8-0      4.62     69.64     18.24     19.01      8.45   2494.82    114.39     52.87
08:25:01 AM   dev8-16      0.18      0.42      2.39     16.08      0.00      6.80      1.20      0.02
08:35:01 AM    dev8-0      1.01     15.78     10.12     25.58      8.02   7865.32    648.12     65.60
08:35:01 AM   dev8-16      0.12      0.00      2.21     18.90      0.00      4.06      0.35      0.00
08:45:01 AM    dev8-0      1.76     21.40     14.44     20.31      2.27   1371.51    118.92     20.98
08:45:01 AM   dev8-16      0.18      0.04      3.23     18.02      0.00      6.50      0.49      0.01


08:45:01 AM       DEV       tps  rd_sec/s  wr_sec/s  avgrq-sz  avgqu-sz     await     svctm     %util
08:55:01 AM    dev8-0      1.92     26.48     16.16     22.17      0.30    153.40     40.71      7.83
08:55:01 AM   dev8-16      0.21      0.24      3.53     17.65      0.00      3.17      0.98      0.02
09:05:02 AM    dev8-0      9.07    155.77     10.56     18.35      3.53    389.80     35.21     31.92
09:05:02 AM   dev8-16      0.95      0.66     15.25     16.79      0.00      1.77      0.76      0.07
09:15:01 AM    dev8-0      2.03     46.09     11.08     28.17      1.71    336.52    115.49     23.43
09:15:01 AM   dev8-16      0.30      0.94      5.12     20.32      0.00      2.59      0.75      0.02
Average:       dev8-0      3.32     94.20     12.90     32.24      4.69   1388.58    114.65     38.09
Average:      dev8-16      0.49      1.47      5.93     15.02      0.00      5.59      0.70      0.03

```

sar CPU, all iowiat:

```
12:00:01 AM     CPU     %user     %nice   %system   %iowait    %steal     %idle
12:05:02 AM     all      0.67      0.00      0.17      0.84      0.00     98.32
12:15:01 AM     all      1.29      0.00      0.26      2.84      0.00     95.61
12:25:01 AM     all      1.10      0.00      0.21      0.71      0.00     97.98
12:35:02 AM     all      1.25      0.00      0.18      0.79      0.00     97.79
12:45:01 AM     all      1.72      0.00      0.25      3.72      0.00     94.31
12:55:01 AM     all      1.13      0.00      0.22     37.36      0.00     61.28
01:05:01 AM     all      0.80      0.00      0.14     45.86      0.00     53.20
01:39:27 AM     all      0.23      1.53      0.51     83.42      0.00     14.31
02:05:58 AM     all      0.14      0.00      0.17     99.69      0.00      0.00
02:15:02 AM     all      1.62      0.23      1.50     96.65      0.00      0.00
12:00:00 AM     all      0.00      0.00      0.00      0.00      0.00      0.00
12:00:00 AM     all      0.00      0.00      0.00      0.00      0.00      0.00
03:39:16 AM     all      1.39      0.11      0.34     34.00      0.00     64.15
03:48:38 AM     all      0.16      0.00      0.20     99.65      0.00      0.00
03:48:39 AM     all     39.82      0.00     43.36     16.81      0.00      0.00
03:55:02 AM     all      2.56      0.08      2.20     95.16      0.00      0.00
04:05:03 AM     all      2.40      0.57      5.06     91.97      0.00      0.00
04:15:04 AM     all      3.06      2.86     11.11     82.97      0.00      0.00
04:25:03 AM     all      1.77      2.69     10.98     84.56      0.00      0.00
04:35:04 AM     all      1.64      2.28     10.91     85.17      0.00      0.00
04:45:04 AM     all      1.64      1.33     10.56     86.47      0.00      0.00
04:55:04 AM     all      1.68      0.75     10.54     87.04      0.00      0.00
05:05:03 AM     all      1.69      0.70     11.06     86.55      0.00      0.00
05:15:03 AM     all      1.78      0.62     10.82     86.78      0.00      0.00
05:25:03 AM     all      1.70      0.02     10.19     88.08      0.00      0.00
05:35:03 AM     all      1.50      0.00      9.59     88.91      0.00      0.00
05:45:02 AM     all      1.60      0.00      9.41     88.99      0.00      0.00
Average:        all      0.96      0.51      3.45     77.86      0.00     17.23

```

To me, this is suggesting that the machine is having problems communicating with the physical disk, and there isnt much I can do.

I have iotop and top running just to make sure I havent got some weird process swamping the disks, it hardly reports any io.

The problem is Microsoft doesnt have technical support for Azure, unless you pay them atleast 120 Euros for support, and since I'm pretty sure this isnt my fault, I'm a bit against that at the moment. Having talked to their support before, its just based in India, and they dont seem to have much technical ability, to be honest. :(

Looking back over my archived syslogs, I can see this also happened couple of months ago, but only a few times, then it stopped.

Can anyone confirm if they also think this would be to do with the physical disk/io rather than anything I can fault find on the VM/Ubuntu side?

If I reboot, it seems to help for a few minutes, then it starts again.

From an Azure point of view, I'm thinking of setting up a new storage account, to try to force it to some new disks maybe, as see if that helps remove the problem, IF I can confirm its a disk problem, as that is going to take me sometime to perform.

Thanks,

Rob.

---

### Post by Rob_Donovan on 2014-08-01
A little bit more info i've noticed:

When the problem happens, it seems that all IO is then frozen for a random amount of time (between 2-15 minutes) 

If you have another session active and just 'cat' a file, it will just sit there for 10 minutes doing nothing.

Watching iotop when this is happening, its reporting 0 IO on the system.

stracing the 2nd process, ie the cat, it freezes on the 'read' command, when it actually trying to get the data from the file.

While this is happening for the 10 minutes or so, the uptime time goes up (about 30+), and processes are queuing up, and they are all in 'D' state, suggesting they are all waiting for disk.

---

