---
title: "[SOLVED] Memory leaking"
date: 2007-11-09
forum: General Help
---

### Post by Jeff78 on 2007-11-09
I appear to be having a memory leak. I am completely new to Ubuntu, only having used it for less than a week, but I have been told it is not normal (as expected) for Ubuntu to be using nearly a gig of memory.

Here's what happens: I restart the computer, everything comes up and runs fine. The system monitor says about 450 MB of ram being used. At that point if I watch the monitor, doing nothing, it climbs, using an extra meg of ram about every two seconds. If I open another program sometimes it climbs quickly and then drops, only to climb back up again eventually at that same rate of about one meg per two seconds. As it approaches a gig of ram used (the amount of memory in my computer), it slows down. [Here]("http://www.gamingw.net/pubaccess/44757/hh.png") is a screenshot of the system monitor if you want to see.

The icons running in the system tray are as follows:
Volume, Klipper, KTorrent, Network, Kopete, Battery Monitor, XChat
...and I am also running Firefox in the foreground, but the leak is present without Firefox running even at system startup.

My computer is a Toshiba Satellite P15-S479, 32bit Intel architecture, nVidia GeForce Go5200 graphics card.

I appreciate any help you can provide.

---

### Post by knutschr on 2007-11-09
What do you see when typing 'top' in terminal or konsole?

---

### Post by Jeff78 on 2007-11-09
> **knutschr said:**
> What do you see when typing 'top' in terminal or konsole?
This:
```
top - 15:27:06 up  2:04,  1 user,  load average: 0.27, 0.30, 0.22
Tasks: 116 total,   1 running, 115 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.0%us,  1.0%sy,  0.0%ni, 96.5%id,  0.0%wa,  0.0%hi,  0.5%si,  0.0%st
Mem:   1035072k total,   994028k used,    41044k free,    18672k buffers
Swap:  2441840k total,      276k used,  2441564k free,   770348k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5631 jeff      15   0 81620  39m  19m S    6  3.9  11:15.72 ktorrent
 5644 jeff      15   0 58392  29m  21m S    0  2.9   0:04.70 guidance-power-
 6726 jeff      15   0  157m  46m  24m S    0  4.6   0:13.23 firefox-bin
 6782 jeff      15   0  2368 1156  876 R    0  0.1   0:00.03 top
    1 root      15   0  2952 1852  532 S    0  0.2   0:01.26 init
    2 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0
    4 root      34  19     0    0    0 S    0  0.0   0:00.22 ksoftirqd/0
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1
    7 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1
    9 root      10  -5     0    0    0 S    0  0.0   0:00.26 events/0
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper
   31 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0
   32 root      12  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1       
```

---

### Post by rsambuca on 2007-11-09
Are you using the nvidia-glx-new driver?

---

### Post by apfsdsdu on 2007-11-09
It's not a leak, the system just uses otherwise unused memory for disk cache. It will be freed if it's needed for something more important.

---

### Post by Jeff78 on 2007-11-09
> **apfsdsdu said:**
> It's not a leak, the system just uses otherwise unused memory for disk cache. It will be freed if it's needed for something more important.
Oh.

Well now I feel really dumb. Thanks for the information, though.

---

