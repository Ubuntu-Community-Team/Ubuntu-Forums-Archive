---
title: "iotop kworker events_power_efficient events_freezable_power"
date: 2020-03-31
forum: General Help
---

### Post by shockedquartz1 on 2020-03-31
Hello all.
I'm new here. I did use the search to answer my own question but came up with nothing.

My question is running iotop. it's spamming these entries constantly
10500 be/4 root        0.00 K/s    0.00 K/s  0.00 %  0.25 % [kworker/u8:0-events_power_efficient]
10500 be/4 root        0.00 K/s    0.00 K/s  0.00 %  0.47 % [kworker/u8:0-events_power_efficient]
10500 be/4 root        0.00 K/s    0.00 K/s  0.00 %  0.24 % [kworker/u8:0-events_power_efficient]
10500 be/4 root        0.00 K/s    0.00 K/s  0.00 %  0.25 % [kworker/u8:0-events_freezable_power_]

Using backtrace, perf doesn't tell me much

This shows off
cat /sys/module/workqueue/parameters/power_efficient
N

Can someone explain what this is doing. My older versions of Ubuntu didn't show this behaviour.

I have an extra spinny HDD for backups I want to sleep when finished.

Thank you for any assistance. :)

---

