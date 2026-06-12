---
title: "Suspend/hibernate problem Thinkpad X1 Carbon 6th gen"
date: 2018-04-19
forum: General Help
---

### Post by vezeli on 2018-04-19
I have problems with suspending function in Ubuntu 16 (kernel 4.13) on Lenovo Thinkpad X1 Carbon. The computer goes into suspend but than starts to overheat, sometimes it wants to come out of suspend and sometimes not. When it comes out of suspend I see that the load averages are very high meaning that it is working and not "relaxing" also it is overheated... As I understand in suspend RAM should continue working but in my case it works too much... 

Also hibernate wasn't working and I found a solution in order to make it work I had to disable Secure boot option in BIOS. After that hibernate worked but not how it should. The computer would go into hibernate but I couldn't make it come out of it, the fan work loudly and the screen remained dark. The only way was to shut it down and turn it on again.

Some people had similar problems on previous X1 Carbon generations and previous Ubuntu versions, they said that upgrading kernel worked for them so I thought that history is repeating itself. I upgraded to kernel 4.14 but this didn't solve the problem...

Anyone know a good substitute for suspend or a fix to this problem? Does anyone else have this problem? It is really annoying to turn off my laptop every time I want to transport it or leave it aside.

---

### Post by andbdrew on 2018-05-04
I also have a problem with 18.04 on 6th gen x1 carbon with suspend/hibernate. I charged up to 100%, unplugged earlier today, closed the lid, and came back several hours later. When I opened the lid, the battery had drained to about 60% and Ubuntu asked to send an error report to canonical about a problem in systemd-journald. I submitted the error report :)

---

### Post by calamari2 on 2018-05-30
> **andbdrew said:**
> I also have a problem with 18.04 on 6th gen x1 carbon with suspend/hibernate. I charged up to 100%, unplugged earlier today, closed the lid, and came back several hours later. When I opened the lid, the battery had drained to about 60% and Ubuntu asked to send an error report to canonical about a problem in systemd-journald. I submitted the error report :)

Anyone get that problem fixed by now? I have exactly the same problems. That is really annoying.

Plus problems like cam sometimes not working, and bluetooth, almost never really.

---

### Post by yannickhk on 2018-05-30
There's a fix. It seems to work but it's quite difficult for a new user like me. I am sticking to hibernate or power off. No suspend for me sadly :(

[https://forums.lenovo.com/t5/Linux-Discussion/X1-Carbon-Gen-6-cannot-enter-deep-sleep-S3-state-aka-Suspend-to/td-p/3998182](https://forums.lenovo.com/t5/Linux-Discussion/X1-Carbon-Gen-6-cannot-enter-deep-sleep-S3-state-aka-Suspend-to/td-p/3998182)

---

### Post by ixot.mh on 2018-09-26
Having the identical issue. The computer appears to be suspended, led is flashing with lid closed, however, it remains active and battery eventually drains.

---

