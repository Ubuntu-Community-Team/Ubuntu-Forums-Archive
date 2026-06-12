---
title: "CPU usage constantly at 100%"
date: 2007-01-15
forum: General Help
---

### Post by nickoli_02 on 2007-01-15
I've just installed Dapper Drake and for some reason the processor usage is consistently at 100% (according to the system monitor). When I open system monitor and try to find what is using so much processor power... nothing is using that much power. There is no process using over, say, 10%. I don't get it...

Anyone have any ideas? I'm somewhat new in the linux game, don't really know where to start with this.

---

### Post by justinjstark on 2007-01-15
It could be some sort of bug in the system monitor.  Try using the "top" command from a terminal and see what it shows.

---

### Post by nickoli_02 on 2007-01-15
here's what I got from running top...

```
top - 19:26:12 up  3:06,  2 users,  load average: 1.03, 1.30, 1.39
Tasks: 102 total,   2 running, 100 sleeping,   0 stopped,   0 zombie
Cpu(s): 55.1% us, 44.9% sy,  0.0% ni,  0.0% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:    515308k total,   477660k used,    37648k free,    21736k buffers
Swap:   273064k total,        0k used,   273064k free,   261288k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4565 root      25   0  2612  572  464 S 97.5  0.1 173:43.98 atieventsd
 4467 root      16   0  111m  35m  12m R  1.7  7.1   6:17.64 Xorg
11146 nwhidden  15   0 39888  14m 9248 S  0.7  2.8   0:02.38 gnome-terminal
 4890 nwhidden  15   0 27664 9432 7120 S  0.3  1.8   0:01.25 gnome-settings-
    1 root      16   0  1564  528  460 S  0.0  0.1   0:01.13 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.08 events/0
    5 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.03 kblockd/0
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  126 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  127 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  129 root      18  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  128 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0
  718 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kseriod

```

so atieventsd is the process eating all my cpu... hum, any ideas now? :)

---

### Post by justinjstark on 2007-01-15
atieventsd, from what I read, is part of the ati graphics driver.

> The driver also includes a program called atieventsd which might take up all of your CPU. I found a thread on a French SUSE forum that suggested removing a socket file would stop the problems. It worked for me:

```
sudo rm /var/run/atieventsd.socket
```

reference: [http://www.marteydodoo.com/2006/08/29/installing-binary-ati-drivers-on-ubuntu-edgy/](http://www.marteydodoo.com/2006/08/29/installing-binary-ati-drivers-on-ubuntu-edgy/)

---

### Post by nickoli_02 on 2007-01-15
Sounds great, just remove this socket file... first I thought I'd create a backup:

```
sudo cp atieventsd.socket atieventsd.socket_bkp
```

but, I get this error:

```
cp: cannot open `atieventsd.socket' for reading: No such device or address
```

???

---

### Post by nickoli_02 on 2007-01-15
I managed to move the atieventsd socket from /var/run to /var instead of creating a backup. I did a restart and I still have the same problem though... atieventsd is still eating my cpu usage, even with the socket file moved down a directory (this should have the same effect as deleting/renaming it, right?)

---

### Post by nickoli_02 on 2007-01-15
Problem solved. I just installed the second newest version of fglrx, and everything seems to work fine.

---

### Post by justinjstark on 2007-01-15
I have no idea what atieventsd is or does and therefore I have no idea what effect removing or moving it would have.


Maybe a [reinstall](http://ubuntuforums.org/showthread.php?t=261153&highlight=atieventsd) of the ati driver would help.

Another thread about it [here](http://ubuntuforums.org/showthread.php?t=231718&highlight=atieventsd).

I haven't found any real definitive answers and as I do not use ATI cards, I can't be of much help.

If you find a solution, please tell us.

Edit: Your post beat mine.  I'm glad you found a solution; thanks for sharing.

---

### Post by mjollnir82 on 2007-05-20
Hi!
I've solved the problem of this damned atieventsd daemon by installing the previous version of my xorg-driver-fglrx.

:popcorn:

I've an ASUS laptop (M6Va wuth an ati x700), Dapper Drake distro, and I downgraded xorg-driver-fglrx package from 8.28.8-1 (from dapper-seveas repository) to 7.0.0-8.25.18+2.6,15,12-28.1 (from dapper-security repository) simply by selecting xorg-driver-fglrx package, and forcing its installation version (from Synaptic menu, Package -> Force version..., and after the downgrade Block Version).

I hope this will be helpful for any guy that have my (now old :guitar:) problem!
Ciao a tutti! \\:D/
Bye!

---

