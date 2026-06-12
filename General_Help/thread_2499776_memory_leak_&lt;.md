---
title: "memory leak |:&lt;"
date: 2024-08-10
forum: General Help
---

### Post by igor-uby on 2024-08-10
I have Ubuntu 22.04.4 LTS (GNU/Linux 6.5.0-45-generic x86_64)
Hardware is ASUS ExpertCenter PN52 (we use it for server).

But it's memory goes up after one day up to 6 Gb, and it seems it will go higher (it went to 7Gb, maybe it would more), just after 1 day.

Issue is in htop, some "gdm3"process is taking most memory. And it's that again. Gnome |:<

This device is sometimes plugged in on monitor, and that's why there's DE. But now lately, we use it to access to it through ssh. So, how to disable DE when no monitor is attached. 
Or why is memory going up so much. 



[IMG]https://i.imgur.com/AWmeUuI.png[/IMG]

---

### Post by TheFu on 2024-08-10
Don't install any GUI on a server.  That's the first lesson to be learned.

Be certain you understand what a program showing memory use is actually showing. It is seldom what you think.  I don't use htop, but check the manpage for that program and read all the memory related parts. Often, what gets displayed by other, similar, tools isn't actually the RAM used.

BTW, Linux made an important choice 20+ yrs ago about memory management to improve performance, at the risk of causing poorly handled out-of-memory errors and crashes.

If you only need a little DE, avoid Gnome and gdm.  There are other options.  In fact, you don't need any DE to have a GUI.  Use openbox and that is usually sufficient for a minimal GUI, if you need one at all.

The best way to remove Gnome stuff is not to have it installed at all.  Install Ubuntu Server (or some other flavor of server).

BTW, please don't post images. You could have easily grabbed the text and posted that instead, saving bandwidth for people who pay by the byte for internet. For example, I use **glances** ... 
```
hadar (Ubuntu 20.04 64bit / Linux 5.15.0-113-generic)                                                                     **Uptime: 35 days, 0:19:18**

4.20/4.20GHz                   CPU       8.9%  nice:     0.0%  ctx_sw:    1K   MEM     15.2%  active:     750M   SWAP      8.6%   LOAD    12-core
CPU  [                 1.0%]   user:     3.2%  irq:      0.0%  inter:   1637   total:  30.7G  inactive:  8.91G   total:   4.10G   1 min:    0.89
MEM  [||              17.2%]   system:   0.9%  iowait:   0.1%  sw_int:   705   used:   5.26G  buffers:    488M   used:     360M   5 min:    0.77
SWAP [|                8.6%]   idle:    95.8%  steal:    0.0%                  free:   25.5G  cached:    8.37G   free:    3.75G   15 min:   0.75

NETWORK                  Rx/s   Tx/s   TASKS 446 (1572 thr), 1 run, 295 slp, 150 oth sorted by disk IO
br0                      11Kb    5Kb
enp3s0                   11Kb    5Kb   CPU%   MEM%  VIRT  RES       PID USER          TIME+ THR  NI S  R/s W/s  Command
lo                       232b   232b   3.3    0.2   375M  67.2M 3343471 tf             0:01 1     0 R    0 0    /usr/bin/python3 /usr/bin/glances
virbr0                     0b     0b   1.3    0.3   1.46G 81.7M    2389 root        2h52:57 18    0 S    ? ?    /usr/lib/xorg/Xorg -nolisten tcp -
                                       0.7    1.6   3.82G 515M  3216230 tf             7:41 198   0 S    ? ?    /usr/lib/firefox-esr/firefox-esr
DefaultGateway                   6ms   0.7    0.8   2.55G 260M  3216389 tf             2:43 27    0 S    ? ?    /usr/lib/firefox-esr/firefox-esr -
                                       0.3    1.0   32.6G 310M  3250376 tf             0:54 30    0 S    0 0    ?page=myorder&action=view&order_id
FILE SYS                 Used  Total   0.3    0.6   2.63G 198M  3216371 tf             1:12 27    0 S    ? ?    /usr/lib/firefox-esr/firefox-esr -
/ (vg01-root01)         7.82G  34.2G   0.3    0.5   1.11T 171M  2022221 tf          2h28:46 24    0 S    0 0    app.asar --no-sandbox --no-zygote
/Backups                 135G   196G   0.3    0.0   13.2M 4.18M    3637 tf             0:13 1     0 S    0 0    /usr/lib/fvwm/2.6.8/FvwmIconMan 13
/d/rom/Data/1TB          125G   196G   0.3    0.0   0     0        1731 root           2:14 1     0 S    ? ?    [jbd2/dm-2-8]
/d/rom/Data/r2           244G  1.48T   0.3    0.0   0     0     3318311 root           0:00 1     0 I    ? ?    [kworker/3:1-events]
/d/rom/export            123G   196G   0.0    1.5   3.74G 482M  2391579 tf         252    h 7    10 S    0 0    /usr/bin/ghb
/d/rom/misc/2TB         1.36T  1.49T   0.0    1.0   1.13T 319M  3251203 tf             0:46 20    0 S    0 0    VQ6B1EUZqoCU04zoRU= --change-stack
/d/rom/raid             1.22T  1.97T   0.0    1.0   2.52G 304M  3216435 tf             0:55 28    0 S    ? ?    /usr/lib/firefox-esr/firefox-esr -
/home (vg01-home01)     9.57G  19.6G   0.0    0.9   2.92G 268M  3216432 tf             0:29 27    0 S    ? ?    /usr/lib/firefox-esr/firefox-esr -
/tmp (vg01-tmp01)        301M  3.86G   0.0    0.8   2.71G 246M  3216472 tf             0:43 27    0 S    ? ?    /usr/lib/firefox-esr/firefox-esr -
/var (vg01-var01)       5.12G  19.5G   0.0    0.7   33.0G 222M  3250414 tf             0:43 33    0 S    0 0    /opt/brave.com/brave/brave --type=
/var/lib/libvirt         131G   134G   0.0    0.6   1.13T 188M  3254409 tf             0:34 19    0 S    0 0    VQ6B1EUZqoCU04zoRU= --change-stack
                                       0.0    0.6   1.13T 178M  3250562 tf             0:05 21    0 S    0 0    VQ6B1EUZqoCU04zoRU= --change-stack
                                       0.0    0.5   2.48G 170M  3216429 tf             0:03 27    0 S    ? ?    /usr/lib/firefox-esr/firefox-esr -
                                       0.0    0.5   2.40G 168M  3216445 tf             0:30 27    0 S    ? ?    /usr/lib/firefox-esr/firefox-esr -
                                       0.0    0.5   1.13T 160M  3250459 tf             0:01 20    0 S    0 0    VQ6B1EUZqoCU04zoRU= --change-stack
                                       0.0    0.5   1.13T 153M  3250538 tf             0:01 22    0 S    0 0    VQ6B1EUZqoCU04zoRU= --change-stack
                                       0.0    0.5   2.39G 146M  3216490 tf             0:17 28    0 S    ? ?    /usr/lib/firefox-esr/firefox-esr -
                                       0.0    0.5   2.38G 146M  3216454 tf             0:01 27    0 S    ? ?    /usr/lib/firefox-esr/firefox-esr -
```
And for an overview of actual memory used:
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           30Gi       4.6Gi        17Gi       237Mi       8.9Gi        25Gi
Swap:         4.1Gi       360Mi       3.7Gi
```
If I flush the buffers ...
```
              total        used        free      shared  buff/cache   available
Mem:           30Gi       3.9Gi        25Gi       237Mi       1.1Gi        26Gi
Swap:         4.1Gi       360Mi       3.7Gi
```
Same exact system, just the RAM used for buffers cleared.
I run a lite GUI on the system, **fvwm**.  Probably a little too hardcore for most people. I've had fvwm config files since the mid-1990s, lovingly handmade over the decades. There's no GUI for that part.  **Openbox** is probably sufficient for most people.

---

