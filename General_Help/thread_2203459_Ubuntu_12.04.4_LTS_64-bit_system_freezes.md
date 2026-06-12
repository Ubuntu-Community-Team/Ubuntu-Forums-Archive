---
title: "Ubuntu 12.04.4 LTS 64-bit system freezes"
date: 2014-02-03
forum: General Help
---

### Post by atanas2 on 2014-02-03
Hello. From about 2 weeks, every day I read posts, try different settings, but nothing... The system totally freeze and no mouse, no keyboard, nothing.

System specification:

MB:[SIZE=2] ASROCK 970 PRO3 [/SIZE]
CPU: [SIZE=2]AMD FX X6 6300[/SIZE]
Video: GeForce GT 440
RAM: 8 GB

I run memtest and no errors. I try with different hard disc with totally new installed ubuntu and nothing.

I try with many nvidia driver version, change kernel version and etc. I also try with this settings: 
```
GRUB_CMDLINE_LINUX="acpi=off"
```

and

```
GRUB_CMDLINE_LINUX="acpi=off noapic nolapic"
```

in grub configuration and no effects.

Kernel version: 3.9.0-030900-generic 

I check syslog, kernel log but I can't find where is the problem.

The system freeze random, sometimes 2-3 times per hour, other time for 4 hours -> 1 time.

---

