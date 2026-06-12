---
title: "Higher load when monitor is off"
date: 2022-05-03
forum: General Help
---

### Post by jultar on 2022-05-03
I'm noticing some weird behaviour on my Ubuntu PC (media PC annex Plex server) after the 22.04 dist upgrade from 21.10, that I can't really explain. As soon as I turn off my monitor, the system load increases to around 0.9 to 1.0 from the regular 0.0 load at idle. As soon as I turn my monitor back on, the load decreases to the regular 0.0, with maybe a little bit of load from regular applications that I'm using.

Example of regular load when my monitor is turned on:

```
top - 15:27:32 up 19 min,  2 users,  load average: 0,01, 0,36, 0,37
Tasks: 348 total,   1 running, 347 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0,0 us,  0,0 sy,  0,0 ni, 99,9 id,  0,0 wa,  0,0 hi,  0,0 si,  0,0 st
MiB Mem :  15922,8 total,  12218,7 free,   1684,8 used,   2019,3 buff/cache
MiB Swap:    980,0 total,    980,0 free,      0,0 used.  13925,8 avail Mem


    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
   2200 <user>    20   0 2008740  90172   8952 S   0,7   0,6   0:05.62 sabnzbdplus
    842 message+  20   0   42432  20860   5012 S   0,3   0,1   0:05.44 dbus-daemon
   2108 plex      20   0  106416  56252  34368 S   0,3   0,3   0:01.01 Plex Media Serv
      1 root      20   0  168444  13864   8236 S   0,0   0,1   0:01.41 systemd
      2 root      20   0       0      0      0 S   0,0   0,0   0:00.00 kthreadd
      3 root       0 -20       0      0      0 I   0,0   0,0   0:00.00 rcu_gp
      4 root       0 -20       0      0      0 I   0,0   0,0   0:00.00 rcu_par_gp
      6 root       0 -20       0      0      0 I   0,0   0,0   0:00.00 kworker/0:0H-events_highpri
      7 root      20   0       0      0      0 I   0,0   0,0   0:00.04 kworker/0:1-events
      8 root      20   0       0      0      0 I   0,0   0,0   0:00.42 kworker/u64:0-flush-253:0
      9 root       0 -20       0      0      0 I   0,0   0,0   0:00.00 mm_percpu_wq
     10 root      20   0       0      0      0 S   0,0   0,0   0:00.00 rcu_tasks_rude_
     11 root      20   0       0      0      0 S   0,0   0,0   0:00.00 rcu_tasks_trace
     12 root      20   0       0      0      0 S   0,0   0,0   0:00.01 ksoftirqd/0
     13 root      20   0       0      0      0 I   0,0   0,0   0:00.43 rcu_sched
     14 root      rt   0       0      0      0 S   0,0   0,0   0:00.00 migration/0
     15 root     -51   0       0      0      0 S   0,0   0,0   0:00.00 idle_inject/0
     16 root      20   0       0      0      0 S   0,0   0,0   0:00.00 cpuhp/0
     17 root      20   0       0      0      0 S   0,0   0,0   0:00.00 cpuhp/1
     18 root     -51   0       0      0      0 S   0,0   0,0   0:00.00 idle_inject/1
     19 root      rt   0       0      0      0 S   0,0   0,0   0:00.22 migration/1
     20 root      20   0       0      0      0 S   0,0   0,0   0:00.00 ksoftirqd/1

<etc>

```

As soon as the monitor is turned off, this list completely changes:

```
top - 15:31:21 up 23 min,  2 users,  load average: 0,95, 0,42, 0,37
Tasks: 343 total,   1 running, 342 sleeping,   0 stopped,   0 zombie
%Cpu(s):  3,7 us,  0,9 sy,  0,0 ni, 94,9 id,  0,1 wa,  0,0 hi,  0,4 si,  0,0 st
MiB Mem :  15922,8 total,  12222,3 free,   1669,4 used,   2031,1 buff/cache
MiB Swap:    980,0 total,    980,0 free,      0,0 used.  13941,0 avail Mem


    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
   1513 <user>    20   0 4100720 371956 132596 S   5,0   2,3   0:37.10 gnome-shell
   1224 <user>    20   0   20960   5852   4116 S   3,7   0,0   0:21.99 dbus-daemon
   1349 <user>    20   0   24,2g  58064  35412 S   2,7   0,4   0:18.57 Xorg
    842 message+  20   0   43852  22304   5012 S   1,0   0,1   0:05.94 dbus-daemon
   1278 <user>    20   0  236592   6640   5912 S   0,7   0,0   0:01.96 gvfs-mtp-volume
  51412 <user>    20   0  486172  46128  35624 S   0,7   0,3   0:00.18 nautilus
  51419 <user>    20   0  379392  28852  21224 S   0,7   0,2   0:00.15 file-roller
   1200 <user>    20   0  388384   8028   6904 S   0,3   0,0   0:01.91 gnome-keyring-d
   1243 <user>    20   0  240752   8372   7300 S   0,3   0,1   0:02.98 gvfsd
   1272 <user>    20   0  389924  10772   8460 S   0,3   0,1   0:02.56 gvfs-udisks2-vo
   1296 <user>    20   0  237552   7276   6472 S   0,3   0,0   0:01.97 gvfs-gphoto2-vo
   1304 <user>    20   0  315332   8092   6944 S   0,3   0,0   0:01.97 gvfs-afc-volume
   1464 <user>    20   0   19912   4660   4192 S   0,3   0,0   0:02.16 dbus-daemon
   1602 <user>    20   0  315008   8564   7236 S   0,3   0,1   0:02.53 gvfsd-trash
   1613 <user>    20   0  477688  15312  11736 S   0,3   0,1   0:02.55 xdg-desktop-por
   1617 <user>    20   0  463176   7160   6492 S   0,3   0,0   0:01.97 xdg-document-po
   1625 <user>    20   0  708228  45680  31904 S   0,3   0,3   0:01.82 xdg-desktop-por
   1631 <user>    20   0  162804   8028   7244 S   0,3   0,0   0:01.18 at-spi2-registr
   1671 <user>    20   0  865076  29752  21656 S   0,3   0,2   0:00.24 gsd-media-keys
   1697 <user>    20   0  341692  24800  17304 S   0,3   0,2   0:00.23 gsd-wacom
   1771 <user>    20   0  238452   8840   6884 S   0,3   0,1   0:01.88 ibus-portal
   1899 <user>    20   0  342336  26036  18876 S   0,3   0,2   0:00.90 xdg-desktop-por
   2148 plex      35  15   62868  42060   9544 S   0,3   0,3   0:02.44 Plex Script Hos
   2200 <user>    20   0 2008740  90172   8952 S   0,3   0,6   0:07.03 sabnzbdplus
      1 root      20   0  168444  13864   8236 S   0,0   0,1   0:01.41 systemd
      2 root      20   0       0      0      0 S   0,0   0,0   0:00.00 kthreadd
      3 root       0 -20       0      0      0 I   0,0   0,0   0:00.00 rcu_gp
      4 root       0 -20       0      0      0 I   0,0   0,0   0:00.00 rcu_par_gp
      6 root       0 -20       0      0      0 I   0,0   0,0   0:00.00 kworker/0:0H-events_highpri
      7 root      20   0       0      0      0 I   0,0   0,0   0:00.05 kworker/0:1-events
      8 root      20   0       0      0      0 I   0,0   0,0   0:00.43 kworker/u64:0-writeback

<etc>

```


All processes seems to be regular processes, but I don't understand what is happening with these processes to constantly be spiking up and what it has to do with turning my monitor off.
Is there anyone with an idea what is happening and how I can prevent this from happening? It seems like my searching skills are lacking to come up with results about this exact problem unfortunately.

PC Specs:
CPU: AMD Ryzen 7 3700X
RAM: 16 GB DDR4 3200 MHz
SSD: Samsung 970 Evo Plus 500GB as boot drive, Samsung 870 QVO 2TB for file storage
GPU: MSI GeForce GTX 1050 TI GAMING X 4G
Mobo: MSI MAG B550 Tomahawk

---

### Post by jultar on 2022-05-04
For those seeing the same behaviour, the issue is with the Desktop Icons NG Gnome extension. After disabling the extension, the issue went away.

---

