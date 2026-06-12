---
title: "Ubuntu 10.04-server stopped detecting all cores"
date: 2013-01-08
forum: General Help
---

### Post by KevinGuancheDarias74 on 2013-01-08
Hi.I started to experience an issue, where my linux stops getting one cpu core. Even /proc/cpuinfo and /sys/devices/system/cpu returns 5 cores. Mi server has 6 CPU cores. I confirmed that is all about an ubuntu issue, since it happends after a while(about days).

A live example can be found at [http://kevinguanchedarias74.tk/phpsysinfo](http://kevinguanchedarias74.tk/phpsysinfo)

I can't continue restarting the server each time this happends. Since it's running some services used by some people...

Edit notice: I restarted the server, so the link above shows 6 cores... for the moment

Addtionally the chcpu command can't be found, but util-linux is installed.

syslog message:

```


Jan  8 12:10:03 KEN74-WEBSERVER kernel: [    0.152038] Switch to broadcast mode on CPU1
Jan  8 12:10:03 KEN74-WEBSERVER kernel: [    0.152079]  #2
Jan  8 12:10:03 KEN74-WEBSERVER kernel: [    0.152080] smpboot cpu 2: start_ip = 8e000
Jan  8 12:10:03 KEN74-WEBSERVER kernel: [    0.244043] NMI watchdog enabled, takes one hw-pmu co$
Jan  8 12:10:03 KEN74-WEBSERVER kernel: [    0.244056] Switch to broadcast mode on CPU2
Jan  8 12:10:03 KEN74-WEBSERVER kernel: [    0.244097]  #3
Jan  8 12:10:03 KEN74-WEBSERVER kernel: [    0.244098] smpboot cpu 3: start_ip = 8e000
Jan  8 12:10:03 KEN74-WEBSERVER kernel: [    0.336053] NMI watchdog enabled, takes one hw-pmu co$
Jan  8 12:10:03 KEN74-WEBSERVER kernel: [    0.336068] Switch to broadcast mode on CPU3
Jan  8 12:10:03 KEN74-WEBSERVER kernel: [    0.336107]  #4
Jan  8 12:10:03 KEN74-WEBSERVER kernel: [    0.336108] smpboot cpu 4: start_ip = 8e000
Jan  8 12:10:03 KEN74-WEBSERVER kernel: [    0.428067] NMI watchdog enabled, takes one hw-pmu co$
Jan  8 12:10:03 KEN74-WEBSERVER kernel: [    0.428082] Brought up 5 CPUs
Jan  8 12:10:03 KEN74-WEBSERVER kernel: [    0.428084] Total of 5 processors activated (30134.41$
Jan  8 12:10:03 KEN74-WEBSERVER kernel: [    0.428081] Switch to broadcast mode on CPU4
Jan  8 12:10:03 KEN74-WEBSERVER kernel: [    0.432140] Switch to broadcast mode on CPU0


```

---

### Post by Doug S on 2013-01-08
I'm only aware of some odd thing where sometimes with AMD processors only one core is detected if there is a USB hub connected. Your situation is a little different because you are detecting 5 out of 6 cores, but still worth looking into.
 
Reference: [http://ubuntuforums.org/showthread.php?t=2084166](http://ubuntuforums.org/showthread.php?t=2084166) (particulalry post #12 and #16)

---

### Post by KevinGuancheDarias74 on 2013-01-30
Ah, don't worry i forgot to post it went fixed by itself

---

### Post by dcstar on 2013-02-01
> **KevinGuancheDarias74 said:**
> Ah, don't worry i forgot to post it went fixed by itself

Then MARK the thread.

---

