---
title: "Xorg process uses 2Gb+ memory"
date: 2014-02-02
forum: General Help
---

### Post by childintime on 2014-02-02
I noticed, that when I freshly boot ubuntu 13.10 Xorg process takes ~60Mb of memory, but after few days it increases to 1Gb, after a week it's over 2Gb which is obviously way too much. At this point I must restart system.

Do you guys have an idea what may be the reason? I searched on google, but found no solution.

---

### Post by tgalati4 on 2014-02-02
Do you have a swap drive or partition set up?

Open a terminal and post the output of:

```
free
```

It sounds like a memory leak.  Does your system slow down to the point of requiring a reboot?  Or do you notice the RAM usage with the system running OK, and reboot anyway?

It's normal for RAM to fill up, but not to the point of using swap or slowing your system down.  A lot of RAM is cached during the normal course of using linux.  That cached RAM is available to the system and gets dumped as needed, but it shows that it is in use.  If your swap gets hit, then things slow down to a crawl.

---

### Post by childintime on 2014-02-02
Yes, it slows down the system completely when used memory rises too much. I have 8Gb or ram, and at one point I closed all programs apart from Chrome with 15 tabs and usage was 5Gb. Then I rebooted, and with same amount of tabs it was around 2.5Gb used.

             ```
total       used       free     shared    buffers     cached
Mem:       8060384    7534888     525496          0      28000    1990340
-/+ buffers/cache:    5516548    2543836
Swap:      4161532      38612    4122920
```

By the way my cache is 2Gb now.

Thanks

---

