---
title: "Stable TurboCore on all cores?"
date: 2020-03-26
forum: General Help
---

### Post by Rayaldi on 2020-03-26
So, I recently installed Ubuntu 18.04.4 and noticed that not all my core can be stable at Throttled State.

I'm using a Laptop that run AMD Richland A8-5550M @ 2.1 GHz, Turbo 3.1 GHz, and monitored my CPU speed using this command

```
[COLOR=#242729][FONT=Consolas]watch -n.1 "cat /proc/cpuinfo | grep \"^[c]pu MHz\""[/FONT][/COLOR]
```

I tried running *sysbench *and get the following result

```
CPU MHz: 13xx
CPU MHz: 13xx
CPU MHz: 29xx
CPU MHz: 29xx
```

the first 2 cores fluctuate between 13xx ~ 14xx while the last 2 cores fluctuate between 28xx ~ 30xx.

My question is, is that how TurboCore works in Ubuntu? Or do I need to do something to get stable TurboCore on all cores?

thx in advance.

Ps: I edited the */etc/default/grub* setting to:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.bapm=1"
```

I also tried to run Minecraft Bedrock Server and get 2.7-ish GHz on all cores for a second when startup then back to normal. When performing demanding action like riding a cart around town full of object the speed of the CPU is the same like above (1.3 and 2.9) making the game lag and stutter.
This didn't happen on Windows, using the same save data and perform the same action, my CPU can achieve 2.8 GHz on all cores and of course, the lag and stutter didn't happen.

EDIT: I forgot to post my *cpupower frequency-info*

```
analyzing CPU 0:  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 4.0 us
  hardware limits: 1.40 GHz - 2.10 GHz
  available frequency steps:  2.10 GHz, 1.90 GHz, 1.70 GHz, 1.40 GHz
  available cpufreq governors: conservative ondemand userspace powersave performance schedutil
  current policy: frequency should be within 1.40 GHz and 2.10 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency: Unable to call hardware
  current CPU frequency: 1.54 GHz (asserted by call to kernel)
  boost state support:
    Supported: yes
    Active: yes
```

---

