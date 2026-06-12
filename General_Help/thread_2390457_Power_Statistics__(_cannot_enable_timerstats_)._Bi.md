---
title: "Power Statistics  ( cannot enable timerstats ). Bionic Beaver"
date: 2018-04-29
forum: General Help
---

### Post by Joao Lacerda on 2018-04-29
Hi Friends, 

Any idea on how to fix this?

Power Statistics-Processor Wakeups is blank showing only this messsage:

```

Processor wakeups per second: GDBus.Error.org.freedesktop.Upower.GeneralError:cannot enable timerstats
```

Thank you for your time.

---

### Post by Doug S on 2018-04-29
I think your issue might be that /proc/timer_stats doesn't exist anymore.
It was removed some time ago. See this [commit]("https://patchwork.kernel.org/patch/9563287/") and this [post]("https://ubuntuforums.org/showthread.php?t=2354739&p=13628119#post13628119").
I found it incredibly useful and am annoyed that it is gone.

---

### Post by fizikz on 2018-09-23
> **Doug S said:**
> I think your issue might be that /proc/timer_stats doesn't exist anymore.
It was removed some time ago. See this [commit]("https://patchwork.kernel.org/patch/9563287/") and this [post]("https://ubuntuforums.org/showthread.php?t=2354739&p=13628119#post13628119").
I found it incredibly useful and am annoyed that it is gone.

Thanks for this explanation. I noticed this same error in Fedora 28 + MATE when trying to view Processor Wakeups in mate-power-manager. Makes sense since it has to do with the linux kernel. 

Disappointing. But at least I can stop looking for a (easy) solution.

---

