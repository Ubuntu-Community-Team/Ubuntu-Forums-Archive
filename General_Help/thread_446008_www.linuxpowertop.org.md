---
title: "www.linuxpowertop.org"
date: 2007-05-16
forum: General Help
---

### Post by thj01 on 2007-05-16
I've stumbled over  [http://www.linuxpowertop.org/](http://www.linuxpowertop.org/), and i'm VERY INTERESTED ind getting more time out of my battery.

I have installed it and i tried to run it but :

> PowerTOP version 1.1 (C) 2007 Intel Corporation

Cn Avg residency (5s) Long term residency avg
C0 (cpu running) (18.4%)
C1 0.0ms ( 0.0%) 0.0ms
C2 1.9ms (51.6%) 1.9ms
C3 2.7ms (12.6%) 2.8ms
C4 3.0ms (17.5%) 3.2ms

Power usage (ACPI estimate) : 13.2 W (2.6 hours left)
No detailed statistics available; please enable the CONFIG_TIMER_STATS kernel option

Suggestion: Enable the CONFIG_NO_HZ kernel configuration option.
This option is required to get any kind of longer sleep times in the CPU. 

Can I enable the CONFIG_TIMER_STATS kernel option.?

Second:

there are a page full of patches but how do i enable/run them??

---

### Post by thj01 on 2007-05-17
anybody?

---

### Post by machoo02 on 2007-05-17
You need to be using kernel 2.6.21 or later (as that version implements the necessary options) to successfully use powertop.  To enable all of the tips/tricks, you will need to compile all of those applications from source and install them.  That would be relatively easy with something like Pidgin, not so easy with something like Xorg.

---

