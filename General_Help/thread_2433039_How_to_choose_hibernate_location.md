---
title: "How to choose hibernate location"
date: 2019-12-12
forum: General Help
---

### Post by geetsce on 2019-12-12
Running XUbuntu for 4 years now (currently 18.04) for home use, I have now upgraded to 16GB RAM, and I ended up with 2 swap locations: a  genuine 16GB swap partition, and additionally a 16GB swap file. Swapping is rarely needed, but when I need it, it mostly fills up at least one of both locations.

There is a lot of info (and noise) on how to choose where to resume from, and I understand the swap partition is the easiest to configure resume from. But before resuming I have to suspend to disk.

 I set the file swap priority higher than the partition swap priority,  so that the swap partition has a better chance of having free space for the hibernation image. Anyway my pc runs smooth with that.

My question is this: can I configure or predict which of both swap locations is used for hibernation,and can I rely on that?

---

### Post by ajgreeny on 2019-12-12
Are you certain that both the swap partition and the swapfile are available at the same time?

What does the command ```
free -mw
``` give as output?  I'm betting it will show 16G total rather than the 32G that you are apparently suggesting you have available, and that if you installed with the swap partition already created it will be that partition that is used.
Can you also show the content of /etc/fstab which may help us, and you, know more about your system.

---

### Post by geetsce on 2019-12-12
Thanks for wanting to help.
> Are you certain that both the swap partition and the swapfile are available at the same time?
Yes they are running fine together, there is no problem with the swapping. But because you need that information, here it is.
```

$ free -mw
[23:38:22]
              total        used        free      shared     buffers       cache   available
Mem:          15928       11719        2294         178          51        1863        3752
Swap:         32770        8908       23862

```

And this is the swap part of my fstab:
```

LABEL=SSWP              none            swap    sw,pri=1,nofail
LABEL=SDATA             /media/sdata    ext4    defaults,noatime,nofail            0    2
/media/sdata/.swapfile  none            swap    sw,pri=2,nofail

```

SSWP is the label of the swap partition, as you may guess, and the .swapfile is just that.

Thinking again about your answer, I realize that you did not explicitely ask for the distribution of used swap over the 2 locations. Probably because you doubt it is possible at all to use 2 locations. I wonder why, swap priority must have some use after all. But here is the swapon output as well. It is in line with the assigned priorities
```

$ swapon --show --bytes
[08:22:56]
NAME                   TYPE             SIZE       USED PRIO
/dev/sda3              partition 17182605312          0    1
/media/sdata/.swapfile file      17179865088 9326981120    2

```

---

