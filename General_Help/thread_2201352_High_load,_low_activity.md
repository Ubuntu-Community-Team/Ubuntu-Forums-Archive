---
title: "High load, low activity"
date: 2014-01-24
forum: General Help
---

### Post by oscar-tiderman on 2014-01-24
Hi,

Saw a strange behaviour on my two week old Ubuntu install, load is about 40 but there is nothing in particular running. Ran a bit of debugging and it turns out I have around 40 processes in D state, all lsof's, just sittting there:

```
maggie@maggie:~$ top -b -n 1 | awk '{if (NR <=7) print; else if ($8 == "D") {print; count++} } END {print "Total status D: "count}'top - 06:23:19 up 1 day, 19:24,  1 user,  load average: 40,13, 39,99, 39,57
Tasks: 482 total,   1 running, 481 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0,4 us,  0,1 sy,  0,0 ni, 99,5 id,  0,1 wa,  0,0 hi,  0,0 si,  0,0 st
KiB Mem:  15861788 total, 15648952 used,   212836 free,   132128 buffers
KiB Swap: 16195580 total,        0 used, 16195580 free, 14590280 cached


  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND
 8446 root      20   0     0    0    0 D   0,0  0,0   0:00.00 192.168.1.66-ma
 8462 root      20   0 12752  104    0 D   0,0  0,0   0:00.04 lsof
 8510 root      20   0 12752  100    0 D   0,0  0,0   0:00.00 lsof
 8560 root      20   0 12752  100    0 D   0,0  0,0   0:00.00 lsof
 8618 root      20   0 12752  108    0 D   0,0  0,0   0:00.00 lsof
 8665 root      20   0 12752  104    0 D   0,0  0,0   0:00.00 lsof
 8713 root      20   0 12752  104    0 D   0,0  0,0   0:00.00 lsof
 8760 root      20   0 12752  104    0 D   0,0  0,0   0:00.00 lsof
 8810 root      20   0 12752  100    0 D   0,0  0,0   0:00.00 lsof
 8857 root      20   0 12752  104    0 D   0,0  0,0   0:00.00 lsof
 8905 root      20   0 12752  100    0 D   0,0  0,0   0:00.00 lsof
 8952 root      20   0 12752  104    0 D   0,0  0,0   0:00.00 lsof
 9000 root      20   0 12752  104    0 D   0,0  0,0   0:00.00 lsof
 9047 root      20   0 12752  104    0 D   0,0  0,0   0:00.00 lsof
 9095 root      20   0 12752  104    0 D   0,0  0,0   0:00.00 lsof
 9144 root      20   0 12752  100    0 D   0,0  0,0   0:00.00 lsof
 9194 root      20   0 12752  108    0 D   0,0  0,0   0:00.00 lsof
 9248 root      20   0 12752  104    0 D   0,0  0,0   0:00.00 lsof
 9305 root      20   0 12752  104    0 D   0,0  0,0   0:00.00 lsof
 9356 root      20   0 12752  100    0 D   0,0  0,0   0:00.00 lsof
 9405 root      20   0 12752  104    0 D   0,0  0,0   0:00.00 lsof
 9453 root      20   0 12752  104    0 D   0,0  0,0   0:00.00 lsof
 9501 root      20   0 12752  108    0 D   0,0  0,0   0:00.00 lsof
 9552 root      20   0 12752  100    0 D   0,0  0,0   0:00.00 lsof
 9955 root      20   0 12752  104    0 D   0,0  0,0   0:00.00 lsof
10010 root      20   0 12752  108    0 D   0,0  0,0   0:00.00 lsof
10062 root      20   0 12752  104    0 D   0,0  0,0   0:00.00 lsof
10114 root      20   0 12752  108    0 D   0,0  0,0   0:00.00 lsof
10166 root      20   0 12752  100    0 D   0,0  0,0   0:00.00 lsof
10214 root      20   0 12752  104    0 D   0,0  0,0   0:00.00 lsof
10264 root      20   0 12752  104    0 D   0,0  0,0   0:00.00 lsof
10311 root      20   0 12752  100    0 D   0,0  0,0   0:00.00 lsof
10362 root      20   0 12752  104    0 D   0,0  0,0   0:00.00 lsof
10408 root      20   0 12752  104    0 D   0,0  0,0   0:00.00 lsof
10463 root      20   0 12752  108    0 D   0,0  0,0   0:00.00 lsof
10508 root      20   0 12752  100    0 D   0,0  0,0   0:00.00 lsof
10556 root      20   0 12752  100    0 D   0,0  0,0   0:00.00 lsof
10606 root      20   0 12752  104    0 D   0,0  0,0   0:00.00 lsof
10660 root      20   0 12752  104    0 D   0,0  0,0   0:00.00 lsof
10710 root      20   0 12752  104    0 D   0,0  0,0   0:00.00 lsof
Total status D: 40



```

Turns out these originate from some cron job (I have not added any cron jobs so this is from Ubuntu):

```
maggie@maggie:~$ pstree init&#9472;&#9516;&#9472;NetworkManager&#9472;&#9516;&#9472;dhclient
     &#9474;                &#9500;&#9472;dnsmasq
     &#9474;                &#9492;&#9472;3*[{NetworkManager}]
     &#9500;&#9472;accounts-daemon&#9472;&#9472;&#9472;2*[{accounts-daemon}]
     &#9500;&#9472;acpid
     &#9500;&#9472;at-spi-bus-laun&#9472;&#9516;&#9472;dbus-daemon
     &#9474;                 &#9492;&#9472;3*[{at-spi-bus-laun}]
     &#9500;&#9472;at-spi2-registr&#9472;&#9472;&#9472;{at-spi2-registr}
     &#9500;&#9472;avahi-daemon&#9472;&#9472;&#9472;avahi-daemon
     &#9500;&#9472;bluetoothd
     &#9500;&#9472;cachefilesd
     &#9500;&#9472;colord&#9472;&#9472;&#9472;2*[{colord}]
     &#9500;&#9472;cron&#9472;&#9472;&#9472;39*[cron&#9472;&#9472;&#9472;sh&#9472;&#9472;&#9472;sessionclean&#9472;&#9516;&#9472;awk]
     &#9474;                                     &#9500;&#9472;lsof&#9472;&#9472;&#9472;lsof]
     &#9474;                                     &#9492;&#9472;xargs]
     &#9500;&#9472;cups-browsed
     &#9500;&#9472;cupsd
     &#9500;&#9472;2*[dbus-daemon]
----snip---

```

I'm no sure how to debug this further, or why these processes even exists. Does anyone have any clues to why or could help me debug why this happens? I'm on Ubuntu 13.10, standard install with Unity, Haswell i7 CPU, 16GB RAM, SSD.

EDIT: This is top with -c:

```
12467 root      20   0 12752  108    0 D   0,0  0,0   0:00.00 /usr/bin/lsof -w -l +d /var/lib/php5
```

---

### Post by justleen on 2014-01-24
I'm not sure how to start debug this further.. I would personally start with that sessionclean cronjob, and check inside what that script  is doing and why that lsof is executed, just to get some insight into why it might hang..


Sorry, not very usefull :(

---

### Post by oscar-tiderman on 2014-01-24
Yeah, thanks, I just removed the cron job for now, I just find it strange that they would hang like that.

---

### Post by justleen on 2014-01-24
What happens if you run the script manually?  Perhaps run it with bash -x, or even a strace
Perhaps thats sheds some light on what's going on

---

### Post by oscar-tiderman on 2014-01-24
Thanks justleen (btw you have 1337 beans :D)
I will strace it later and post result. I am not running php or apache so I guess it gets stuck since there are no open files from php processes, in that case it's a bug.

---

