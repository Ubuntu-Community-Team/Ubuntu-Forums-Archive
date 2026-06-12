---
title: "swap space used, despite free RAM"
date: 2007-03-10
forum: General Help
---

### Post by laachlaan on 2007-03-10
Is it normal to have 173MB of swap space used when I still have plenty of RAM left?

This is the output of free

```

             total       used       free     shared    buffers     cached
Mem:       2059244    1729424     329820          0      65596    1199008
-/+ buffers/cache:     464820    1594424
Swap:      2971984     173636    2798348

```

What is using that swap space, and why?

---

### Post by Jmccaffrey on 2007-03-10
When a memory page is swapped, it will usually not be unswapped until it is requested.  This means that you can be sitting with alot of free space and still have some swap used until that page is requested again.

---

### Post by rocketman768 on 2007-03-10
He's right. Stuff could have been swapped to disk when you were low on memory and just stayed there since nothing has requested the data contained in those chunks of memory yet. It's normal.

---

### Post by OldGaf on 2007-08-10
I also get this quite often, but I don't think I have ever used even close to all my ram. I also shut down my system daily so that would clear everything out. Is there a config somewhere that controls the use of swap vs ram?

[IMG]http://www.nialm.com/karamba.png[/IMG]

---

### Post by 9a3eedi on 2007-08-10
as far as I know, there's a tool that allows you to configure the kernel's "swappability", i.e. how frequently the kernel uses swap for memory.

but I don't know anything more than that ._.

---

### Post by ThrobbingBrain66 on 2007-08-10
[http://www.brunolinux.com/06-Fine_Tuning_Your_System/Swappiness.html](http://www.brunolinux.com/06-Fine_Tuning_Your_System/Swappiness.html)

Use swappiness with caution.

---

### Post by OldGaf on 2007-08-13
> **ThrobbingBrain66 said:**
> [http://www.brunolinux.com/06-Fine_Tuning_Your_System/Swappiness.html](http://www.brunolinux.com/06-Fine_Tuning_Your_System/Swappiness.html)

Use swappiness with caution.

Thanks to ThrobbingBrain66 and 9a3eedi

---

### Post by simoncullen on 2007-09-02
This is *really* frustrating me!  I have 2GB installed on a Core 2 Duo running Feisty---and my machine uses plenty of swap while there's over 1GB of free ram!
> 
top - 06:16:25 up 55 min,  1 user,  load average: 1.90, 1.83, 4.68
Tasks: 171 total,   2 running, 169 sleeping,   0 stopped,   0 zombie
Cpu(s): 16.1%us,  3.3%sy,  0.0%ni, 70.4%id,  9.2%wa,  0.7%hi,  0.3%si,  0.0%st
Mem:   2075804k total,  1229676k used,   846128k free,    79148k buffers
Swap:  1759076k total,   430800k used,  1328276k free,   405200k cached


I've set swappiness to 5 and it still does it.....It actually runs rather sluggishly without it.  It just wont utilize the ram that is available.  I've let my BIOS do the ram check at startup and there's no apparent problems.... 

Confoundedly,

Simon

---

### Post by simoncullen on 2007-09-02
Hmm.... So top and htop report less than 800mb ram use, while free -m reports:

simon@frege:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2027       1983         43          0         37       1223
-/+ buffers/cache:        722       1304
Swap:         1717        423       1294
simon@frege:~$                      

Very strange....Is it odd that I should be using swap with 2GB of ram?  How can I find what's gobbling it up if nothing is reported in top?

Simon

---

### Post by scrooge_74 on 2007-09-02
ps -ax

---

### Post by bogolisk on 2007-09-02
> **laachlaan said:**
> Is it normal to have 173MB of swap space used when I still have plenty of RAM left?

This is the output of free

```

             total       used       free     shared    buffers     cached
Mem:       2059244    1729424     329820          0      65596    1199008
-/+ buffers/cache:     464820    1594424
Swap:      2971984     173636    2798348

```

What is using that swap space, and why?

I think it's quite normal and good. My guess is:
[list]
[*] The default virtual memory split in ubuntu kernel is kernel-1G/user-3G
[*] You have more ram than the kernel could directly map (2G while the kernel virtual space is 1G)
[*] The high 1G is used as hi-memory (not directly mapped) by the kernel. Part of it can be mapped into the last 128M of the virtual kernel space.
[*] The swap is used for automatic inter-zone page migration (moving LRU pages into high memory)
[/list]

So using the swap would make the kernel use the entire 2G more efficiently. Disable swap would definitely make things slower because you basically disable inter-zone page migration.

Ok, it was just a guess, so don't take my word for it! Go ask a kernel dev!

---

### Post by simoncullen on 2007-09-02
> **scrooge_74 said:**
> ps -ax

But that wont tell me about how much *memory* the processes are using?

---

### Post by reacocard on 2007-09-02
> **simoncullen said:**
> But that wont tell me about how much *memory* the processes are using?

I think he meant 'ps aux' which does show mem, but if its not in top I doubt it'll give you any more info. I have 1GB and swippiness is 0, swap usually stays at 0 but occasionally a few megs get swapped out, but never more than 1-2% of my 1.2GB swap.

You can force what was swapped out back into ram by doing
```
sudo swapoff -a 
sudo swapon -a
```

---

### Post by simoncullen on 2007-09-02
Things are sort of making sense now:

> 
simon@frege:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2027       1971         55          0         58        902
-/+ buffers/cache:       1010       1016
Swap:         1717          0       1717
simon@frege:~$


I've switched swappiness to 0 and done swapon/swapoff.  Swap has stayed at zero as you can see.  Interestingly, where *free* says I've 55mb free, *top* says:

> 
Cpu(s): 10.3%us,  2.3%sy,  0.0%ni, 85.7%id,  1.3%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   2075804k total,  2020332k used,    55472k free,    59520k buffers
Swap:  1759076k total,      732k used,  1758344k free,   919776k cached


So I presume you were right: the kernel only maps 1G ......  Anyway, things are running *Very* snappy here indeed.  Incredibly---immediately noticeably---faster than before I played with this---i.e., when swappiness was set to 60.

Cheers!

---

### Post by Gremlinzzz on 2007-09-02
type in terminal sysinfo

---

### Post by simoncullen on 2007-09-02
> **Gremlinzzz said:**
> type in terminal sysinfo

System information report, generated by Sysinfo: 3/09/2007 8:46:13 AM
[http://sysinfo.r8.org](http://sysinfo.r8.org)

SYSTEM INFORMATION
	Running Ubuntu Linux, the 4.0 release.
	GNOME: 2.18.1 (Ubuntu 2007-04-10)
	Kernel version: 2.6.20-16-generic (#2 SMP Thu Jun 7 20:19:32 UTC 2007)
	GCC: 4.1.2 (i486-linux-gnu)
	Xorg: 7.2.0 (04 April 2007)
	Hostname: frege
	Uptime: 0 days 3 h 25 min

CPU INFORMATION
	GenuineIntel, Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz
	Number of CPUs: 2
	CPU clock currently at 996.000 MHz with 2048 KB cache
	Numbering: family(6) model(15) stepping(6)
	Bogomips: 3366.08
	Flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm

MEMORY INFORMATION
	Total memory: 2027 MB
	Total swap: 1717 MB

---

### Post by Gremlinzzz on 2007-09-02
Is your swap smaller than your memory swap is suppose to be at least double the ram
mine is 
memory 1001 MiB
swap 2321 MiB
ubuntu created my swap

---

### Post by amorangi on 2007-11-03
That seems crazy to me - 1GB kernel/ 1GB User seems rather shortsighted. I'm having the same issue - 2Gb of RAM, and a huge amount in swap when there's over a GB free RAM. I just ran an experiment turning off the swap altogether, then started up a couple of VMs, and indeed RAM usage would not go over 1024MB, just a lot of HDD activity. I'll try the swappiness parameter, but does anyone have any other ways so that I can actually use all my 2GB RAM? Otherwise it would seem what's the point of have anything over 1GB?

---

