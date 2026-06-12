---
title: "System Monitor never shows memory usage above 74%"
date: 2014-12-08
forum: General Help
---

### Post by Ralph L on 2014-12-08
I have a Dell Latitude D610 with 2 G of memory.  When I run System Monitor, it never shows more than 74% usage.  When I do "cat /proc/sys/vm/swappiness", I get a value of "1" returned, which I think means that swapping should be delayed until I have only 1% of memory left.  However, with about 72% memory usage (according to System Monitor) Ubuntu starts swapping things out, when I launch a new application.  This is, of course, painfully slow.  I have even tried "sudo swapoff -a", and it still swaps, when memory is around 72% full.

Can anybody explain why System Monitor memory usage never goes above 74%.  It it that the other 26% of memory is used for something else that System Monitor doesn't know about?  Or is Ubuntu (my system is 12.04) not using all available memory for some reason?

---

### Post by grahammechanical on 2014-12-08
What System Monitor does not show is memory set aside as cache. I think that you will find that the 70 - 74% figure is inclusive of cache memory. You might want to install System Load Indicator. That will put an app indicator in the top panel and show the usage of various system resources including memory, cache and swap.

I only have 1 GB of memory and my 14.10 system rarely uses more than 70%. In 12.04 70% was the amount of memory used out 1 GB with just System Monitor loaded. But improvements in the way Linux handles memory mean that from 14.04 onwards memory usage starts at 50%.

The system will always set some memory aside as cache memory so that as memory needs increase the system has memory ready to hand. Cache memory gets smaller as memory usage increases but there seems to always be some in reserve. So, it is my guess, that although System Monitor is showing something like 74% memory usage the actual memory usage is much less. The usage level stays the same as there is still cache memory in reserve.

So, why is swap being used when applications are loaded? Perhaps the OS is reserving a parking space in case it really needs to start paging data into and out of the hard disk swap partition. Although I have only 1GB of RAM I would not describe the loading of applications as painfully slow. Of course applications do not load instantaneously. I do not expect that. Hard disks have set data transfer rates. Although I have heard that SSDs give a good impression of speed. I also think that the graphic adapter has a part to play in all of this.

We might think that with you having twice the RAM as me the percentage memory used should be at least half of my memory usage. It seems that things do not work that way. Memory is there to be used. Or, perhaps it is better to say: "Claimed/Reserved."

Regards.

P.S. With only Chromium open System Load Indicator is showing 456 MB used; 336 MB cache in reserve out of my 1 GB RAM and 420 MB swap in use.

---

### Post by Ralph L on 2014-12-10
Thanks for the response.  I appreciate it.

I googled "system load indicator" and saw some year 2012 remarks that it had a memory leak.  Do you know if that has been fixed?  I am afraid to use it until it is fixed.

I stumbled upon the program "top".  It displays system resource usage.  It is invoked using Terminal as ```
top
```.  On my system with swappiness set to 1 it showed 91% memory usage rather the 50% that System Monitor showed.  So I guess, if I believe "top", I am really using my memory.  I wonder why top and system monitor should show such a big difference.  Are they measuring different things, or does one just have a bug?  Any thoughts?

---

### Post by nerdtron on 2014-12-10
```
~]# free -m
             total       used       free     shared    buffers     cached
Mem:          7687       7662         25          0        116       7240
-/+ buffers/cache:        305       7382
Swap:            0          0          0

 
```

No bugs. It's designed that way.
See the output of free memory? The first entries (used: 7662MB) are the one shown in the top command. While the system monitor uses the second entries (used 305MB). The system monitor does not take into account the buffers/cache that is also stored on the RAM.

---

### Post by Ralph L on 2014-12-10
nerdtron:  Thanks for the response. 

I still had some question even after your explanation so I went to this site:  [http://www.linuxnix.com/2013/05/find-ram-size-in-linuxunix.html](http://www.linuxnix.com/2013/05/find-ram-size-in-linuxunix.html) and they gave a very good example explaining the relationship among the different numbers output by free.  Also, I went to this site [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/) which gave a good explanation of disk caching.  

However, I still don't understand linux buffering and how ram used for buffering is immediately available to an application.  I understand the use of buffering for things like sending data through a network, where the cpu may produce a batch of data much faster than the network can transmit it so the cpu puts the data in a buffer and the network slowly transmits that data and empties the buffer.  However, I don't understand how such a buffer can be made instantly available to an application.  The way I understand buffering, the buffer must be emptied before the ram can be reused and this takes time.  So the ram is not immediately available.  Would you explain how a buffer can be made immediately available to an application?

In addition, I am still puzzling over why my System Monitor ram usage never gets over 74% if the other 26% is available for immediate use by releasing disk caches and releasing buffers.  I am speculating that the other 26% can NOT be made immediately available, because buffers can't be immediately released, and because some applications probably require permanent buffers.  Also, maybe the system requires a certain minimum amount of disk caching to keep the system running fast.  Any explanation would be appreciated!

---

