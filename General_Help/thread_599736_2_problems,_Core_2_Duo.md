---
title: "2 problems, Core 2 Duo"
date: 2007-11-01
forum: General Help
---

### Post by Denn1s on 2007-11-01
Hello everybody, i needed help with some issues, any help will be apreciated, thank you

first my specs:

Core 2 Duo E4400 @ 2.00 GHz
1 GB RAM
Xubuntu Gutsy Gibbon
uname -rv : 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 20

first problem, high processor usage:

a classic, kacpid is consuming 70% of one of the CPUs at all times, a part of top:
```

  PID USER      PR   NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
   32   root      10  -5     0    0       0 R       76     0.0    43:20.11   kacpid      


```

passing acpi=off to grub turns that process off, but also one of the cores so only one proccesor is used, passing acpi=ht at boot results in system hanging. 

second problem, high RAM ussage:

top and free report very high RAM usages, nearly 800 MB after some time, starts at 600 after i log in, i think it is a lot for a "lightweight" system as xfce, however, gnome-system monitor reports from as low as 100 MB to as high as 300 MB at most, which would be very cool, also ps aux shows the same as the system monitor, wich one is ok? is xubuntu really using that much RAM?

thanks for your help

---

### Post by bingoUV on 2007-11-01
Post the output of free, and the contents of /proc/meminfo .

Without that it seems that memory usage could be buffers.

---

### Post by Denn1s on 2007-11-01
free upon a fresh reboot:
```

total       used           free      shared        buffers     cached
Mem:       1019168     498108     521060          0            8796     205876
-/+ buffers/cache:     283436     735732
Swap:      2088408          0    2088408

```

i think its just cache.... 

proc meminfo:

```

dennis@AMI:~$ cat /proc/meminfo
MemTotal:      1019168 kB
MemFree:        454072 kB
Buffers:         10272 kB
Cached:         225292 kB
SwapCached:          0 kB
Active:         213896 kB
Inactive:       181564 kB
SwapTotal:     2088408 kB
SwapFree:      2088408 kB
Dirty:             112 kB
Writeback:           0 kB
AnonPages:      159928 kB
Mapped:          57532 kB
Slab:            24148 kB
SReclaimable:    12304 kB
SUnreclaim:      11844 kB
PageTables:      10036 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   2597992 kB
Committed_AS:   380228 kB
VmallocTotal: 34359738367 kB
VmallocUsed:      8960 kB
VmallocChunk: 34359729147 kB

```

wath does cached and buffered memory exactly do?

---

### Post by bingoUV on 2007-11-02
Memory usage is of (at least) two kinds  : memory required by running programs, and buffers.

The memory required by running programs is necessary (if physical ram is not available, they will use the swap space i.e. hard disk). If the running set of processes (set of processes that run at a given time that are scheduled typically in succession repeatedly)  does not fit in physical ram and needs swap ; the system will run extremely slowly. A high amount of this category of memory usage could be considered harmful, especially in lightweight distributions like xubuntu.

If you have spare memory, linux kernel ( like windows kernels since NT) will cache your disk access in memory. This typically would only use spare memory, and filling up even GBs of ram in this category of usage should be considered proper utilization of available ram. This will speed up your subsequent disk accesses. As you will be aware, ram is hundreds of times faster than hard disk.

If you have issues with high memory usage in ubuntu, post the output of free, and contents of /proc/meminfo to this forum. This might uncover some bug in ubuntu, or misconfiguration on your part.

---

### Post by Denn1s on 2007-11-02
thank you for the explanation, its informative, ill see if i can make acpi=ht work regarding the other problem, i had a ubuntu-feisty-32 instalation where acpi=ht worked and it took both cores without the kacpid proccess,if i enable acpi=ht in xubuntu-gutsy-64 it fails to boot when attempting to load something like a battery.ko module (im running a desktop)

EDIT

if i boot up without uSplash i get a terminal, this is the error:

```

Error inserting battery (/lib/modules/2.6.22-14-generic/kernel/drivers/acpi/battery.ko): No such device

```

is i do startx from here i get, failed to initialize HAL, and no internet

since the problem is different i started a new thread, if you hav some help regarding the battery.ko problem phease answer [here]("http://ubuntuforums.org/showthread.php?p=3704589#post3704589")

---

