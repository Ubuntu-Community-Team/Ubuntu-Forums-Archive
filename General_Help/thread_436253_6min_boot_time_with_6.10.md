---
title: "6min boot time with 6.10?"
date: 2007-05-07
forum: General Help
---

### Post by HunterMaximus on 2007-05-07
I've got a 6.10 server install, and it hangs at "Uncompressing Linux... Ok. Booting the kernel." for several minutes, then when it boots up i get the following message before the standard MOTD and login prompt:
```
[   509.252524] sis630_smbus 0000:00:02.0: SIS630 comp. bus not detected, module not inserted.
```

The bootup seems to usually take about 6 mins from power to login prompt.

I have a custom compiled kernel, following the instructions here: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)
The only option I changed was to enable expanding RAID5 expand with mdadm. Everything else is the same as the previous kernel.

I can't remember if I had this problem before the custom kernel, but I think so (its a headless server, so I just turn on the power and log in remotely via ssh).

The specs are:
AMD Duron stock @ 800MHz
384MB SD RAM
ECS K7S5A - note: this doesn't have an sis630 chip on it, may have somethign to do with that message?
nVidia TNT2

Any ideas how I can fix this problem?

---

### Post by HunterMaximus on 2007-05-08
bump.... anybody?

---

### Post by HunterMaximus on 2007-05-11
Still no ideas? Is there a better forum/section for this?

---

