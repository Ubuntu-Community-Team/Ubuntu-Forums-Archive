---
title: "Ubuntu 8.04 is running a little slow..."
date: 2008-04-25
forum: General Help
---

### Post by Crafty Kisses on 2008-04-25
I usually didn't have problems like this with Ubuntu 7.10, is it possible since Ubuntu 8.04 has more features it takes up more RAM?

It's a little slow, but then again it just came out, so that also could be an issue.

I looked into this issue on Google, and some other people have had some troubles like mine, it's really weird, Gutsy ran flawless. Hardy runs good too, but just not as good as Gutsy, again I hope this can be fixed with an update.

My theory is Compiz has something to do with it, but again I could be wrong, anyone else experiencing these problems?

Here's my "top" output:
```
top - 12:34:56 up  1:52,  2 users,  load average: 0.80, 1.09, 1.15
Tasks: 104 total,   2 running, 102 sleeping,   0 stopped,   0 zombie
Cpu(s): 28.4%us,  5.3%sy,  0.0%ni, 65.3%id,  0.0%wa,  0.3%hi,  0.7%si,  0.0%st
Mem:   2075060k total,   741352k used,  1333708k free,    31836k buffers
Swap:  1646620k total,        0k used,  1646620k free,   441436k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 7746 codename  20   0 99.4m  22m  12m S 12.6  1.1   2:05.61 audacious          
 7915 codename  20   0 64672  31m 8328 R 11.3  1.5   1:10.17 compiz.real        
 5351 root      20   0 83240  37m 9.8m S  6.6  1.8   6:41.10 Xorg               
 7935 codename  20   0  170m  57m  20m S  5.3  2.8   0:37.85 firefox            
 8183 codename  20   0 86104  19m  11m S  2.0  1.0   0:00.70 gnome-terminal     
 5796 codename  20   0 30528 5808 3344 S  1.0  0.3   0:06.37 pulseaudio         
 7386 codename  20   0  110m  25m  16m S  1.0  1.3   0:10.02 pidgin             
 5813 codename  20   0 15212 2728 1808 S  0.7  0.1   0:19.64 gnome-screensav    
    1 root      20   0  2844 1688  544 S  0.0  0.1   0:01.40 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.14 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 khelper            
   42 root      15  -5     0    0    0 S  0.0  0.0   0:00.10 kblockd/0          
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
```

30% of my RAM is in use when I'm sitting on my desktop sometimes, it's really odd.

Here are the specs of this Computer, (I have 2): Intel Celeron 2.4 GHZ, nVidia GeForce 6800GT, 2 GB of RAM and 2 HDD's.

I'm pretty sure that should run OK with Hardy Heron, but I could be wrong. Again I usually don't post about problems like this, but I'm really stumped on this one, I've done a lot of research, and tried several things to solve this issue, still nothing. 

Again I'm aware Ubuntu 8.04 is brand new on the Ubuntu Circuit, so I don't want to seem annoying or anything. Thanks for the help in advance.

This is also a upgrade not a fresh install.

---

### Post by hbayar_morph on 2008-04-27
I think i have a same problem. My spec is pretty good:

C2D e6850 @3.0GHz
2GB Ram
8800gtx 768MB
RaptorX HDD.

Shouldn't slow, but I feel little bit lagging, which is not in 7.10
Hope it'll fixed via update

---

### Post by Crafty Kisses on 2008-04-27
> **hbayar_morph said:**
> I think i have a same problem. My spec is pretty good:

C2D e6850 @3.0GHz
2GB Ram
8800gtx 768MB
RaptorX HDD.

Shouldn't slow, but I feel little bit lagging, which is not in 7.10
Hope it'll fixed via update
Yeah, I really hope so.

---

