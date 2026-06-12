---
title: "How to disable the disk write cache in Ubuntu 13.10?"
date: 2014-05-11
forum: General Help
---

### Post by simgineer on 2014-05-11
Based on [this]("https://stackoverflow.com/questions/20215516/disabling-disk-cache-in-linux") answer I used: **sudo hdparm -W 0 /dev/sda** to try and disable the write cache on my Ubuntu 13.10 box running on bare hardware. Additionally in /etc/hdparm.conf I also uncommented from the line **#write_cache = off**

When I run: **hdparm -i /dev/sda** i get:

```
...
UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
AdvancedPM=yes: unknown setting WriteCache=disabled
Drive conforms to: unknown:  ATA/ATAPI-3,4,5,6,7
...
```

Regardless, I still get these insanely high write through puts that are higher than my read which leads me to believe my write cache is still active. What is the correct way to disable the write cache on a Ubuntu 13.10 system??? i'm attaching a screenshot of a utility I've written that shows my write bw to be insanely high (2.2GB/s) until the write cache is filled up (looks like 1.2gb). Any feedback is greatly appreciated.

[IMG]http://i.stack.imgur.com/LFc31.png[/IMG]

---

