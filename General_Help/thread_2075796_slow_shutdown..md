---
title: "slow shutdown."
date: 2012-10-24
forum: General Help
---

### Post by techvish81 on 2012-10-24
i have installed ubuntu 12.10 on an ocz agility3 ssd , startup is very fast but shutdown is slow and same as it was on a hdd.   i've read several threads regarding slow shutdown in 12.04 and previous versions , is there any workaround to fix it in 12.10?

---

### Post by techvish81 on 2012-10-25
bump

---

### Post by techvish81 on 2012-10-26
it halts for sometime and after that some disk activity happens before shutdown, if it matters.

---

### Post by bond17_007 on 2012-10-28
I am having similar issue. I had 12.04 on this Dell 1558 8GB Ram, 128 SSD Agility 4. 
on 12.04 it booted in less than 10 seconds and shutdown in less than 2.

I upgraded to 12.10. Startup time is fairly similar but now shutdown time has increased to about 5-7 seconds. when i try to look at the screen while shutdown process, i see that it says .." killing all other processes..." then it hangs in there for seconds, i quick see word "...[FAIL], it flashes quickly that i cannot read that it failed on. 

I have been trying to hunt down log but no luck..

any suggestions?

---

### Post by zarquod on 2013-01-06
Bump!

I have exactly the same problem with a 120 GB OCZ Agility 3 SSD. Slightly worse, even: Booting aborts because the root partitions journal can't be restored.

---

### Post by rnerwein on 2013-01-06
> **zarquod said:**
> Bump!

I have exactly the same problem with a 120 GB OCZ Agility 3 SSD. Slightly worse, even: Booting aborts because the root partitions journal can't be restored.
hi
to all - in which universe are all of you  living. what's five or ten seconds or what is the definition of slow ?????
cheers

---

### Post by Rocklobster690 on 2013-01-06
Check the logs and tell us what the fail message was please.

Looking through the forum theres a few threads on this:

[http://ubuntuforums.org/showthread.php?t=2070963](http://ubuntuforums.org/showthread.php?t=2070963)
[http://ubuntuforums.org/showthread.php?t=2066573](http://ubuntuforums.org/showthread.php?t=2066573)

I think this is the bug - [https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/1061639](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/1061639)

Try stopping the service networking before shutting down.. or follow this article  - [http://www.hecticgeek.com/2012/10/speed-up-ubuntu-shutdown-process/](http://www.hecticgeek.com/2012/10/speed-up-ubuntu-shutdown-process/)

---

