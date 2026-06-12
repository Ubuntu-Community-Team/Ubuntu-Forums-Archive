---
title: "ZRAM and configuration"
date: 2017-10-18
forum: General Help
---

### Post by jbmukund on 2017-10-18
[FONT=arial]Hi 


I am trying to setup ZRAM on ubuntu 4.4 kernel. I can load and create zram based swap devices fine as you can see below.


# apt-get install zram-config 


cat /proc/swaps 
Filename                Type        Size    Used    Priority
/dev/sda3                               partition    16638972    0    -1
/dev/zram0                              partition    2036816    0    5
/dev/zram1                              partition    2036816    0    5
/dev/zram2                              partition    2036816    0    5



How can I make it work. I tried running memtester and load it with stress
stress --vm-bytes $(awk '/MemFree/{printf "%d\n", $2 * 0.9;}' < /proc/meminfo)k --vm-keep -m 1

It does not look like it is being used.


I notice that 'used' count in /proc/swaps does not bump at all. I even tried 'vmstat 1 100 ' while running stress and memtester and did not see any change in SO and SI. 
What am I missing?



Thanks,
M J




[/FONT]

---

### Post by HermanAB on 2017-10-18
Well, usually, Linux doesn't use swap at all, so that is likely why you don't see anything happening.

So, you need to do something that consumes all available RAM, thus forcing the system to swap.

---

### Post by jbmukund on 2017-10-18
> Linux doesn't use swap. 
Why do you think do.
#top shows 
   KiB Swap: 31346936 total,    20016 used, 31326920 free. 11183868 cached Mem

it is using swap but not a lot.

Do we have to do anything make to make Linux the SWAP more except changing swappiness in /proc/? tried that, did not help.
what would that be beyond using stress 90% of RAM and memtester is running too.

M J

---

