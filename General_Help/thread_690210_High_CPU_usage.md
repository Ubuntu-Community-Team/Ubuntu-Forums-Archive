---
title: "High CPU usage"
date: 2008-02-07
forum: General Help
---

### Post by kenmiles on 2008-02-07
Can anyone please help with this problem with Ubuntu 6.10.
My CPU usage keeps going from about 8 -100 % and I can't see the reason why.
I have attached my running processes and a snapshot of the CPU usage.
Thanks in advance for any help, Kenneth.
[http://kmiles.co.uk](http://kmiles.co.uk)

---

### Post by jaytek13 on 2008-02-07
If you go to the command line and type "top" it will give you more detailed information about what processes are using how much CPU.

---

### Post by kenmiles on 2008-02-07
> **jaytek13 said:**
> If you go to the command line and type "top" it will give you more detailed information about what processes are using how much CPU.

Thank for that, this is the output from top -

top - 14:25:40 up  1:26,  1 user,  load average: 0.97, 0.70, 0.59
Tasks: 136 total,   2 running, 133 sleeping,   0 stopped,   1 zombie
Cpu(s): 57.0%us,  6.0%sy,  0.0%ni, 35.7%id,  0.0%wa,  0.0%hi,  1.3%si,  0.0%st
Mem:   1035660k total,   740636k used,   295024k free,    30252k buffers
Swap:        0k total,        0k used,        0k free,   458792k cached

The highest is from apt-index-watch which goes at times as high as 46% but the total of all precesses is never more than 60% recorded here.

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 7308 root          20   0 18760  14m  11m R    32.6        1.4   0:00.98 apt-index-watch
 5416 kenneth  15   0  205m  63m  27m S   10.0       6.3   0:59.25 firefox-bin
 4127 root         15   0 47536  19m 4932 S      3.7        1.9   3:58.20 Xorg
 4945 kenneth  -51   0 21876 7452 5432 S    0.7       0.7   0:21.62 artsd
 5311 kenneth   16   0 55180  21m  16m S    0.7       2.1   7:32.80 gnome-system-mo
 5308 www-data  15   0  7960 2496 1560 S    0.3       0.2   0:00.04 apache2
 5635 kenneth   15   0 34592  16m  12m  S   0.3       1.6  0:03.52 konsole
 7151 kenneth   16   0  2252 1100  824 R      0.3         0.1   0:00.66 top

Can you see any reason here please.
Thanks, Kenneth.

---

### Post by Cybergod on 2008-02-07
I suggest installing htop and running it.  It is excellent :)

---

### Post by SOULRiDER on 2008-02-07
Yeah, the info htop displays is far more readable than tops.
Install htop
```
sudo aptitude install htop
```
Then run it and press f6 to sort all processes and select CPU.

---

### Post by kenmiles on 2008-02-07
> **Cybergod said:**
> I suggest installing htop and running it.  It is excellent :)

I did-
 sudo killall apt-index-watcher
and that cured it, now back to normal cpu load.
Thanks, Kenneth.

---

### Post by Abandon on 2008-02-07
Do:

sudo /etc/init.d/apt-index-watcher stop 

or choose to remove it while booting with:

update-rc.d apt-index-watcher remove

Oh..it' s apt- index watcher what is giving you this cpu peak:

[B]apt-index-watcher  -  Watches  for  changes  in  the  APT index and run
       actions when it happens.

DESCRIPTION
       Watches for changes in the APT index and run actions when it happens.
       The only action it currently runs is to rebuild the apt-front  indexes.
       In the future, apt-index-watcher will support a proper hook system.[/B]

---

### Post by kenmiles on 2008-02-07
> **Abandon said:**
> Do:

sudo /etc/init.d/apt-index-watcher stop 

or choose to remove it while booting with:

update-rc.d apt-index-watcher remove

Oh..it' s apt- index watcher what is giving you this cpu peak:

[B]apt-index-watcher  -  Watches  for  changes  in  the  APT index and run
       actions when it happens.

DESCRIPTION
       Watches for changes in the APT index and run actions when it happens.
       The only action it currently runs is to rebuild the apt-front  indexes.
       In the future, apt-index-watcher will support a proper hook system.[/B]

Thanks for that info, have now removed it as you suggest.
Regards, Kenneth.

---

### Post by plucky on 2008-02-07
Kenneth,

> Swap: 0k total, 0k used, 0k free, 458792k cached Have you noticed that you are running without a swap partition?

Just thought I would mention it.

---

### Post by kenmiles on 2008-02-07
> **plucky said:**
> Kenneth,

 Have you noticed that you are running without a swap partition?

Just thought I would mention it.

That has always confused me!
I have a swap partition of 1.44gb which was set when Ubuntu was installed but it is never used.
Regards, Kenneth.

---

