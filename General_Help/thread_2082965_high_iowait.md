---
title: "high iowait"
date: 2012-11-11
forum: General Help
---

### Post by Unguidedone on 2012-11-11
When i load a song in vlc player my system monitor graph shows huge cpu spike (running 4 core i3)  and iowait goes form 0%1%2% -  30 to 50%

there is also heavy memory usage 
when i was running 10.10 i would never go above like 900 meg for ram out of 4 gig and 12.04 is using like 95% ram


what is the best action to take here?

---

### Post by 2F4U on 2012-11-11
Ubuntu uses the RAM as a cache. What would it be worth having 4 GB of RAM and only using 900 MB of it, while the rest is sitting unused? If there is a real need for additional RAM, Ubuntu releases some of the cache, so that other applications can claim it.

---

### Post by Unguidedone on 2012-11-11
```
Linux 3.2.0-32-generic (julio-Lenovo-B570)     11/11/2012     _x86_64_    (4 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          12.01    0.15    2.43    0.95    0.00   84.47

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sda               8.76       130.03       159.10   41112995   50305460

julio@julio-Lenovo-B570:~$ 

```

at random times iowait spikes while cpu remains at like 10-20%

---

