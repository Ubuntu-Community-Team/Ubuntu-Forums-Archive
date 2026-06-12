---
title: "mdadm rebuild very slow with default /proc/sys/dev/raid/speed_limit_min"
date: 2014-08-27
forum: General Help
---

### Post by bsphere on 2014-08-27
Ubuntu 14.04.1
Atom 330
AT3N7A

Rebuilding a raid5 array is extremely slow with the default /proc/sys/dev/raid/speed_limit_min

If I leave it at default (1000) and the max at whatever the default is (20000?) the rebuild speed is roughly 2MB/s. When I increase the max to 500MB/s and the min to 50MB/s the speed increases to about 60-70MB/s.

Is this by design and if not what do I need to tweak? I assume that rebuilding an array is a priority, you dont want to wait 10 days when it can take 10 hours.

---

### Post by TheFu on 2014-08-27
Been there too - used this: [http://www.cyberciti.biz/tips/linux-raid-increase-resync-rebuild-speed.html](http://www.cyberciti.biz/tips/linux-raid-increase-resync-rebuild-speed.html)

---

### Post by Daniel_Bannoura on 2014-12-18
Hello,

I'm having speed issues with reshaping a raid array and have tried dozens of tweaks with no luck. When I first built the array I used 7 new drives, 3TB each and was getting about 30Mb/s sync speed that completed in about 3 days. Then I added another 3TB drive using mdadm add, grow (total of 8 drives now) which worked fine, but now my reshape sync speed hovers around 4Mb/s and will take 12,000 min to complete. I've gone through every suggestion and tweak I can find and nothing has an impact on the speed. CPU hovers around 20% and memory usage is at about 20-30% (4GB DDR3 1066). 

I'm somewhat new to Linux and know my way around, but I must be missing something! 

Any ideas would be much appreciated!

---

### Post by TheFu on 2014-12-18
Best to start a new thread to ask a new question. A different person = new thread. Use a good, descriptive, thread title.

Also - an **exact list** of the previously attempted commands and options would be helpful. We cannot tell what you've tried already from "every suggestion and tweak I can find" since it often turns out that sometimes people aren't so good at finding resources online.

*I'm new to linux and know my way around? * That is counter-intuitive.  I'm new to RAID myself, just been doing it for 15 yrs, but mdadm only for 12 yrs. Switched from RAID5 to RAIDz2 to RAID1 over the years. Much happier now with a simpler config. ;)

RAID level, current and attempted disk params?  Any hdparms?  The controllers involved may be important too.

Also showing the exact command used to get performance stats would be helpful. Sometimes the testing method is wrong or other parts of the infrastructure get in the way.

---

