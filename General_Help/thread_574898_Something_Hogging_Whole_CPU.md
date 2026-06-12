---
title: "Something Hogging Whole CPU"
date: 2007-10-13
forum: General Help
---

### Post by pmorton on 2007-10-13
Whenever I rsync or copy files from one drive to another (running Feisty), the system goes all but dead on me, the panel system monitor reporting  "Processor: 100% in use". Gnome System Monitor (or  'ps aux'  at the console) turns up no process using more than 2% CPU (and that's the Gnome System Monitor itself). Something is behaving badly, but I can't see what it is. Is there another way to detect the culprit?

---

### Post by taurus on 2007-10-13
```
top
```

---

### Post by HermanAB on 2007-10-13
Use the bandwidth limit parameter to prevent Rsync from hogging all resources:
--bwlimit=KBPS

Cheers,

H.

---

### Post by pmorton on 2007-10-13
Herman AB <Use the bandwidth limit parameter to prevent Rsync from hogging all resources:
--bwlimit=KBPS>

Done that, but makes no difference. The transfer continues very slowly, and everything else is almost  frozen.

---

### Post by pmorton on 2007-10-13
> **taurus said:**
> ```
top
```

Thanks, taurus, for the advice to use 'Top'. But, like Gnome System monitor, it doesn't identify any  process which is hogging CPU, and it doesn't list 'rsync' as a process, which surprises me. 

I've restricted the rsync transfer rate to 500KB/sec as suggested by HermanAB (thanks), and that has  worked to unfreeze the system for other use. But the gnome panel System Monitor still reports CPU usage swinging between 50% and 100%; which contradicts Top (Top accords with the CPU useage advised by System Monitor itself of a couple of percent).

Rsync is still transferring files at a horribly slow rate.  I'm transferring big .tif files (each 50MB). According to the specified transfer rate of 500KB/sec they should each take approx 1.5min each to transfer. But they're taking far longer - 8  minutes or more. Is the swap file involved in transferring files of this size?  I don't recall having this problem of slow copying with another (more widely used, but vastly inferior ;-) ) operating system (I'm copying between local SATA drives, by the way).

---

### Post by Jamezracer on 2008-05-31
I'm having the exact same problem, this is transferring large amounts of data to an external usb hard drive. at first the transfer was at about 15-20 MB/s and using almost all of my cpu (2.2ghz dual core), computer lagged but still usable. For some reason transferring a different set of files, although also avi, resulted in 3MB/s transfer (painfully slow) and my cpu being completely used, firefox took a whole minute to open under this condition. seems like an unnecessary set of calculations is being made when doing this very simple file transfer task which windows does not seem to have a problem with.

---

