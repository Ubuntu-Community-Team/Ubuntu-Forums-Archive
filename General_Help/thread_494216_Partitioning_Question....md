---
title: "Partitioning Question..."
date: 2007-07-06
forum: General Help
---

### Post by jayson.rowe on 2007-07-06
Ok, I type ```
df -l
``` in to my console, and I don't get a listing for my / partition...is this normal, or is something screwed up?

```
Filesystem           1K-blocks      Used Available Use% Mounted on
varrun                 1030364        68   1030296   1% /var/run
varlock                1030364         0   1030364   0% /var/lock
procbususb             1030364       120   1030244   1% /proc/bus/usb
udev                   1030364       120   1030244   1% /dev
devshm                 1030364         0   1030364   0% /dev/shm
lrm                    1030364     38972    991392   4% /lib/modules/2.6.20-16-generic/volatile
/dev/hda1               112883     27592     79269  26% /boot
/dev/hda4             77775620   1127044  72697792   2% /home
/dev/hdb2             19228308    176208  18075348   1% /home/jayson/downloads
/dev/hdb4            200941896   1379176 189355424   1% /home/jayson/music
/dev/hdb3             19228308    176200  18075356   1% /home/jayson/videos
/dev/hda3             28834744   2420096  24949924   9% /usr
```

---

### Post by jayson.rowe on 2007-07-07
nobody has any feedback on this? I'm probably worrying over nothing, as I doubt my machine would boot if my / partition wasn't mounted, but I want to know for sure...BTW my root partition is on /hda2 which isn't showing up in the list anywhere either.

---

