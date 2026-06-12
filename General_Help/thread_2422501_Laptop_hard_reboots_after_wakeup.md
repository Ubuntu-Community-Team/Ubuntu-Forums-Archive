---
title: "Laptop hard reboots after wakeup"
date: 2019-07-08
forum: General Help
---

### Post by mirek2 on 2019-07-08
Hi, I am dealing with a weird issue for the last couple of months but now i finally have some time to track it down. 

I have Xubuntu 18.04.2 (installed and switched to KDE env. however that doesn't matter, issue persists) and I'm running it on Thinkpad E540 with Core i7 4702mq, 2x8GB RAM and 256GB m.2 SSD  + 1TB HDD. 
My issue is that after wakeup the fan ramps up (but the CPU temp is ok, ~50°C, checked using [FONT=lucida console]sensors[/FONT]) and after 30 seconds the computer shuts down instantly and starts again (and then during boot it does a filesystem check, so it's a hard shutdown). 
I've tried updating the kernel to the latest version which was 4.20 at the time but it didn't solve the problem. For my sanity I updated again to 5.1 today but same thing. I am not really sure how to track this issue down. 

I'm attaching dmesg log saved few seconds before it shuts down for both the old 4.20 kernel and new 5.1. but I didn't find anything useful there.
[ATTACH]283583[/ATTACH]

Thanks in advance for any help

---

