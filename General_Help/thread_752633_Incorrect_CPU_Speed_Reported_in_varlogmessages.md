---
title: "Incorrect CPU Speed Reported in /var/log/messages"
date: 2008-04-11
forum: General Help
---

### Post by stuffman on 2008-04-11
Hello everyone,
I run xubuntu 7.10 on my computer with an Intel 3.0GHz P4 HT processor, running on a PCChips board with 1GB of PC3200 RAM.  In my /var/log/messages file I found the following line:

Apr  9 10:46:59 desktop kernel: [    0.000000] Detected 2000.341 MHz processor.

I'm curious if there's any way to get this to register properly, and whether I'll get any performance benefits if I can figure out how to force it to 3GHz (real or perceived).  If anyone has any ideas I would appreciate the feedback.  I'm going to look into an updated bios revision, but always hate to mess with a machine that is otherwise working great.  Thanks,



Shawn

---

### Post by pointone on 2008-04-11
This may be due to some power saving mode.

Try:

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
```

---

### Post by stuffman on 2008-04-12
Weird, but when I try going to /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies, it gives me 'No Such File Or Directory'.  The path is only valid up to cpu0, there is no cpufreq subdirectory.  Any ideas?

---

### Post by stuffman on 2008-04-17
^bump^

---

