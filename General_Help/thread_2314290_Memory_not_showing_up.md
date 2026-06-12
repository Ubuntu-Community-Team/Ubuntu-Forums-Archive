---
title: "Memory not showing up"
date: 2016-02-19
forum: General Help
---

### Post by bizhat on 2016-02-19
Hi,

I have 6 GB RAM in My PC. But ubuntu shows only 4 GB.

```

boby@hon-pc-01:~ $ free -m
             total       used       free     shared    buffers     cached
Mem:          3943       2961        981         33        142        910
-/+ buffers/cache:       1908       2035
Swap:         6134          0       6134
boby@hon-pc-01:~ $ cat /proc/meminfo
MemTotal:        4038064 kB
MemFree:         1018708 kB
Buffers:          150004 kB
Cached:           955596 kB
SwapCached:            0 kB
Active:          1886912 kB
Inactive:         856936 kB
Active(anon):    1643264 kB
Inactive(anon):    32108 kB
Active(file):     243648 kB
Inactive(file):   824828 kB
Unevictable:        5200 kB
Mlocked:            5200 kB
SwapTotal:       6282236 kB
SwapFree:        6282236 kB
Dirty:              2952 kB
Writeback:             4 kB
AnonPages:       1643336 kB
Mapped:           289728 kB
Shmem:             33736 kB
Slab:              94252 kB
SReclaimable:      50352 kB
SUnreclaim:        43900 kB
KernelStack:        5440 kB
PageTables:        44256 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     8301268 kB
Committed_AS:    6343240 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      313444 kB
VmallocChunk:   34359419388 kB
HardwareCorrupted:     0 kB
AnonHugePages:    323584 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:      214528 kB
DirectMap2M:     3971072 kB
boby@hon-pc-01:~ $ uname -a
Linux hon-pc-01 3.13.0-77-generic #121-Ubuntu SMP Wed Jan 20 10:50:42 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
boby@hon-pc-01:~ $ 

```

If i run MemTest at the boot screen of Ubuntu, it shows 2 GB of RAM on 3 Slots (6 GB Total).

[img]http://i.imgur.com/bTGPJVh.jpg[/img]

In MemTest there is cached says 4 GB. 

Any idea why 6 GB is not showing up ?



Thanks,

Boby

---

### Post by gordintoronto on 2016-02-20
The most likely answer is that you are using a 32-bit operating system. Run: uname -a

---

### Post by bizhat on 2016-02-20
Thanks for the reply. OS is 64 bit, i did posted in first post, since it was last part of CODE, it was under the scroll bar.


```

boby@hon-pc-01:~ $ uname -a
Linux hon-pc-01 3.13.0-77-generic #121-Ubuntu SMP Wed Jan 20 10:50:42 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
boby@hon-pc-01:~ $

```

---

### Post by Bucky Ball on 2016-02-20
Ok. Brand new sticks? Make sure they are seated correctly. Pull them and put them back in once or twice, even if they appear to be seated fine. 

If still no joy, and this might sound crazy but it is an age old trick, rub the contacts of the RAM sticks lightly with a pencil eraser (rubber, whatever you call it in your part of the world). A layer of 'stuff/manufacturing residue' can be left on the contacts from the factory and that can cause problems. The eraser gets rid of it.

After this, try again. Still no joy? Start swapping sticks and check the RAM and slots one by one. Pull all RAM. First stick in first slot only. Working? Shutdown. Second stick in first slot only. Working? Go through all sticks solo in the first slot. If all clear, move on to the second slot.

You'll soon find out if it is a RAM stick or a RAM slot (worse, obviously). If the former, back to the shop. If the latter, the same if the machine is under warranty. 

Good luck.

---

### Post by bizhat on 2016-02-21
Thanks for the reply, its old PC. I will try that.

```

boby@hon-pc-01:~ $ free -k
             total       used       free     shared    buffers     cached
Mem:       4038064    3546784     491280     116228      14084     390676
-/+ buffers/cache:    3142024     896040
Swap:      6282236     237744    6044492
boby@hon-pc-01:~ $

```

If only 2 ram stick is using, how 4 GB ram is calculated as 4038064 kB RAM ? That means 1 GB of RAM =  1009516 kB ?  This number changed because mother board use up some RAM or it should show exact amount ? 

My mother board is "SABERTOOTH X58", that have no build in graphics (i seen some mother board with built in graphics share video memory with system ram).

---

