---
title: "Problem with kswapd0"
date: 2012-11-20
forum: General Help
---

### Post by pshepherd on 2012-11-20
I have recently done a clean install of minimal Quantal with XBMC and after awhile (>10mins) I am getting a problem with kswapd0 eating 100% of cpu time .. see top o/p:

[PHP]xbmc@zotac:/proc$ top
top - 21:23:35 up 21:51,  1 user,  load average: 1.04, 1.05, 1.05
Tasks:  88 total,   3 running,  85 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.0 us, 50.3 sy,  0.0 ni, 49.7 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:    896028 total,   752404 used,   143624 free,    16580 buffers
KiB Swap:  5301412 total,        8 used,  5301404 free,   518272 cached

  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND
   27 root      20   0     0    0    0 R  99.8  0.0 108:15.63 kswapd0
 1329 xbmc      20   0  272m 146m  44m S   1.0 16.8 150:23.89 xbmc.bin
   44 root      20   0     0    0    0 S   0.3  0.0   0:07.23 scsi_eh_1
    1 root      20   0  3496 1504  836 S   0.0  0.2   0:00.52 init
    2 root      20   0     0    0    0 S   0.0  0.0   0:00.02 kthreadd
    3 root      20   0     0    0    0 S   0.0  0.0   0:00.99 ksoftirqd/0
    6 root      rt   0     0    0    0 S   0.0  0.0   0:00.14 migration/0
    7 root      rt   0     0    0    0 S   0.0  0.0   0:00.26 watchdog/0
    8 root      rt   0     0    0    0 S   0.0  0.0   0:00.13 migration/1
   10 root      20   0     0    0    0 S   0.0  0.0   0:01.59 ksoftirqd/1
   11 root      rt   0     0    0    0 S   0.0  0.0   0:00.16 watchdog/1
   12 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 cpuset
   13 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 khelper
   14 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kdevtmpfs
   15 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 netns
   17 root      20   0     0    0    0 S   0.0  0.0   0:00.14 sync_supers
   18 root      20   0     0    0    0 S   0.0  0.0   0:00.00 bdi-default
   19 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 kintegrityd
   20 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 kblockd
   21 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 ata_sff
   22 root      20   0     0    0    0 S   0.0  0.0   0:00.00 khubd
   23 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 md
   26 root      20   0     0    0    0 S   0.0  0.0   0:00.02 khungtaskd
   28 root      25   5     0    0    0 S   0.0  0.0   0:00.00 ksmd
xbmc@zotac:/proc$ free
             total       used       free     shared    buffers     cached
Mem:        896028     752032     143996          0      16580     518272
-/+ buffers/cache:     217180     678848
Swap:      5301412          8    5301404
[/PHP]

I was previously running XBMC + Maverick on the same box without this problem.

I have tried sudo swapoff -a and usage stays the same.

Google indicates I am not the first to see this and it may be bug.  What are my options a) revert to Precise?, b) wait for a kernel fix?

TIA, paul

---

### Post by Diar16335502 on 2013-02-13
Just out of interest are you running encrytion. I didn't have this problem until I enabled encryption and see it when dealing with large files on the encrypted areas.

---

### Post by rnerwein on 2013-02-13
> **pshepherd said:**
> I have recently done a clean install of minimal Quantal with XBMC and after awhile (>10mins) I am getting a problem with kswapd0 eating 100% of cpu time .. see top o/p:

[PHP]xbmc@zotac:/proc$ top
top - 21:23:35 up 21:51,  1 user,  load average: 1.04, 1.05, 1.05
Tasks:  88 total,   3 running,  85 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.0 us, 50.3 sy,  0.0 ni, 49.7 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:    896028 total,   752404 used,   143624 free,    16580 buffers
KiB Swap:  5301412 total,        8 used,  5301404 free,   518272 cached

  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND
   27 root      20   0     0    0    0 R  99.8  0.0 108:15.63 kswapd0
 1329 xbmc      20   0  272m 146m  44m S   1.0 16.8 150:23.89 xbmc.bin
   44 root      20   0     0    0    0 S   0.3  0.0   0:07.23 scsi_eh_1
    1 root      20   0  3496 1504  836 S   0.0  0.2   0:00.52 init
    2 root      20   0     0    0    0 S   0.0  0.0   0:00.02 kthreadd
    3 root      20   0     0    0    0 S   0.0  0.0   0:00.99 ksoftirqd/0
    6 root      rt   0     0    0    0 S   0.0  0.0   0:00.14 migration/0
    7 root      rt   0     0    0    0 S   0.0  0.0   0:00.26 watchdog/0
    8 root      rt   0     0    0    0 S   0.0  0.0   0:00.13 migration/1
   10 root      20   0     0    0    0 S   0.0  0.0   0:01.59 ksoftirqd/1
   11 root      rt   0     0    0    0 S   0.0  0.0   0:00.16 watchdog/1
   12 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 cpuset
   13 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 khelper
   14 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kdevtmpfs
   15 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 netns
   17 root      20   0     0    0    0 S   0.0  0.0   0:00.14 sync_supers
   18 root      20   0     0    0    0 S   0.0  0.0   0:00.00 bdi-default
   19 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 kintegrityd
   20 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 kblockd
   21 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 ata_sff
   22 root      20   0     0    0    0 S   0.0  0.0   0:00.00 khubd
   23 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 md
   26 root      20   0     0    0    0 S   0.0  0.0   0:00.02 khungtaskd
   28 root      25   5     0    0    0 S   0.0  0.0   0:00.00 ksmd
xbmc@zotac:/proc$ free
             total       used       free     shared    buffers     cached
Mem:        896028     752032     143996          0      16580     518272
-/+ buffers/cache:     217180     678848
Swap:      5301412          8    5301404
[/PHP]I was previously running XBMC + Maverick on the same box without this problem.

I have tried sudo swapoff -a and usage stays the same.

Google indicates I am not the first to see this and it may be bug.  What are my options a) revert to Precise?, b) wait for a kernel fix?

TIA, paul
hi
i don't realy think that this can be a problem but the relationship of your swap-size and real memory (Swap:      5301412 -  Mem:        896028) makes me a little confused.
cheers
ups - can it be that you are a running a 32-bit system and the system got problems with > 4GB ??
just a idea: try your swap-size with gparted. 
because a value of 5301412 do not fit in 4194304. that's only a stomage feeling of me 
cheers

---

