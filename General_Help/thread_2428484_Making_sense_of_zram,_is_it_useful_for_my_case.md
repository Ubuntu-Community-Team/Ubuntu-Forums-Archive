---
title: "Making sense of zram, is it useful for my case?"
date: 2019-10-04
forum: General Help
---

### Post by sammichpg on 2019-10-04
Hi everyone, I'm running kubuntu 18.04 with HWE and kernel 5.0 on a laptop with a quadcore i7 8550u and 16gb of ram. I'm a biologist and my work involves processing large uncompressed microscopy images using a java based program (FIJI aka ImageJ).
I often bump into ram limits and I tried enabling zram without success. I tried playing with several swappiness, vfs cache pressure settings but the behavior is always the same: no swapping occurs until I hit almost full ram utilization, then the system begins thrashing, I have extremely high cpu utilization and eventually I have to powercycle.

The output of my zramctl is the following
```
NAME       ALGORITHM DISKSIZE  DATA COMPR TOTAL STREAMS MOUNTPOINT                                                                                                                                                                                                             
/dev/zram3 lzo             2G    8K  336B   16K       8 [SWAP]                                                                                                                                                                                                                 
/dev/zram2 lzo             2G   12K  517B   16K       8 [SWAP]
/dev/zram1 lzo             2G    8K  338B   16K       8 [SWAP]
/dev/zram0 lzo             2G  184K  9,2K   72K       8 [SWAP]


```

My swappiness is set at 10 (I tried 60, 80, 100 to no avail)
```
cat /proc/sys/vm/swappiness
10
```

I have no other swapping partitions:
```
cat /proc/swaps
Filename                                Type            Size    Used    Priority
/dev/zram0                              partition       2038304 236     32767
/dev/zram1                              partition       2038304 8       32767
/dev/zram2                              partition       2038304 8       32767
/dev/zram3                              partition       2038304 256     32767
```


Shouldn't ZRAM be useful for my use case?

---

### Post by Artim on 2019-10-04
Linux is built to use all available RAM before it turns to other resources.  This might be helpful:
[Linux Ate My RAM]("http://linuxatemyram.com")!

---

### Post by sammichpg on 2019-10-06
> **Artim said:**
> Linux is built to use all available RAM before it turns to other resources.  This might be helpful:
[Linux Ate My RAM]("http://linuxatemyram.com")!

That was not relevant to my issue, thanks for trying.

For future reference of other people encountering this issue, I managed to isolate the culprit to TLP. Some setting changed by TLP must not play nice with zram. I devactivated TLP, rebooted and tried to edit a 4500x4200x200frames rgb tiff in ImageJ and it did not choke! The system is actually running smooth and is perfectly responsible. I'm currently sitting at 14.8gb of used ram with another 3.5 sitting nicely compressed in the zram devices.

---

### Post by sudodus on 2019-10-07
Thanks for sharing your solution :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED. This can help other users with the same or similar problems.

---

