---
title: "My ram is nearly full all the time"
date: 2016-05-21
forum: General Help
---

### Post by Evil Wayz on 2016-05-21
I am running 16.04LTS, 4.4 generic kernel, with CInnamon 3 as my windows manager.  My computer has been bogging down recently, I thought maybe my cpu was overloading.  But it's not.  I have a dual core and both cores are running at around 30%, with occasional spikes to around 50%.  But my ram is running full 7.5 out of 7.8gb, constantly. .  My swap file is 9.3 gbs, yet only half a gig is being used.  Is there anything I can do about this or is my computer hardware getting old?

---

### Post by pqwoerituytrueiwoq on 2016-05-21
how much ram do you have? (edit you say you have 8gb, wonder if it all registers)
the output of these commands would be helpful
```
top -n 1 -o %MEM
cat /proc/meminfo
```

---

### Post by Evil Wayz on 2016-05-21
command 1 yields 
```
top - 22:06:59 up 2 days,  4:37,  1 user,  load average: 3.67, 4.27, 4.53
Tasks: 269 total,   3 running, 266 sleeping,   0 stopped,   0 zombie
%Cpu(s): 18.1 us,  4.9 sy,  0.2 ni, 67.0 id,  8.0 wa,  0.0 hi,  1.7 si,  0.0 st
KiB Mem :  8175104 total,   136744 free,  6731156 used,  1307204 buff/cache
KiB Swap:  9782268 total,  8632800 free,  1149468 used.   769260 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 2959 wolf      20   0 3457644 2.057g  87208 S   0.0 26.4  50:36.00 chrome      
 2094 wolf      20   0 2143192 598620  32128 S   5.6  7.3 138:15.99 cinnamon    
 2683 wolf      20   0 2188536 561296  36768 S   0.0  6.9 156:03.27 chrome      
 2790 wolf      20   0 2547288 538744 124456 S   0.0  6.6 116:04.97 chrome      
26081 wolf      20   0 1553688 348196  60888 S   0.0  4.3   5:58.19 chrome      
 2942 wolf      20   0 1327584 334832  71588 S   0.0  4.1  30:01.25 chrome      
 2931 wolf      20   0 2085572 266284  40652 S   0.0  3.3  23:03.94 chrome      
 2197 wolf      20   0 1562368 235832   9460 S   0.0  2.9   6:02.67 nemo        
 8676 wolf      20   0 1668612 233164   8864 S  16.7  2.9 314:24.19 transmissi+ 
 2134 wolf      39  19 1652072 213244   6716 S   0.0  2.6   3:27.49 tracker-ex+ 
 8340 wolf      20   0  968800 200744  29944 S   0.0  2.5   0:36.22 chrome      
 2786 wolf      20   0 1046576 180052   9272 S   0.0  2.2  27:36.22 chrome      
 2192 wolf      20   0 1363536 155228   5312 S   0.0  1.9   2:13.95 gnome-soft+ 
 2247 wolf      20   0 2100860 138972      0 S   0.0  1.7   3:08.21 dropbox     
 6208 wolf      20   0 1415512 129664   5104 S   5.6  1.6   4:25.57 mpv         
 1059 root      20   0  906212 107380  74384 S   5.6  1.3  72:53.38 Xorg        
 2774 wolf      20   0  667056 106052  43020 S   0.0  1.3  86:41.82 chrome      
wolf@shaitan:~$ 

```

Command 2 yields 
```
wolf@shaitan:~$ cat /proc/meminfo
MemTotal:        8175104 kB
MemFree:          148416 kB
MemAvailable:     713168 kB
Buffers:          162304 kB
Cached:           873016 kB
SwapCached:        29020 kB
Active:          5996792 kB
Inactive:        1583360 kB
Active(anon):    5649224 kB
Inactive(anon):  1269144 kB
Active(file):     347568 kB
Inactive(file):   314216 kB
Unevictable:        3284 kB
Mlocked:            3284 kB
SwapTotal:       9782268 kB
SwapFree:        8627800 kB
Dirty:             30608 kB
Writeback:            16 kB
AnonPages:       6530948 kB
Mapped:           504056 kB
Shmem:            373764 kB
Slab:             202888 kB
SReclaimable:     143808 kB
SUnreclaim:        59080 kB
KernelStack:       13456 kB
PageTables:        84872 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:    13869820 kB
Committed_AS:   15799604 kB
VmallocTotal:   34359738367 kB
VmallocUsed:           0 kB
VmallocChunk:          0 kB
HardwareCorrupted:     0 kB
AnonHugePages:    776192 kB
CmaTotal:              0 kB
CmaFree:               0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:     1275744 kB
DirectMap2M:     7112704 kB

```

---

### Post by SeijiSensei on 2016-05-21
Linux generally uses all available RAM and allocates what isn't needed for programs to disk caching.  That "1307204 buff/cache" figure indicates you have 1.3 GB devoted to caching.  If you run more programs, the cache will become smaller. 

The biggest memory hog on your system is clearly Chrome.  Have you tried other browsers like Firefox?

---

### Post by Evil Wayz on 2016-05-22
I actually switched to Chrome because firefox got bloated. Guess I'll switch back and see what happens.

---

### Post by pqwoerituytrueiwoq on 2016-05-22
right now my firefox is using 7% of my ram, firefox will use more ram if it is available and scale reasonably but if you don't account for scaling that would be 14% on your system, you may want to give [chromium](apt:chromium-browser) a try (it is basically google chrome without the bloat)
you can get pepper flash in firefox, i think this method will give it to chromium also
[http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html](http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html)

---

### Post by oldos2er on 2016-05-22
Have you changed the default swappiness value? The default is 60, which is too high in my opinion. See [https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F) for information on changing it.

Also see [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by Evil Wayz on 2016-05-22
Swappiness is 5.  If I switch to Chromium will all my setting move when I sign in or do I have ti import my bookmarks, reinstall extensions, etc?

---

### Post by oldos2er on 2016-05-22
Do you mean switching to Chromium from Chrome? I want to say it will automagically pull in any existing settings, but it's been a long time since I've used Chromium. Don't know for sure.

---

