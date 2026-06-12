---
title: "powertop in feisty... how to enable kernel options?"
date: 2007-05-17
forum: General Help
---

### Post by vav on 2007-05-17
Intel has released powerTOP, which helps optimize battery life in linux... 
[http://www.linuxpowertop.org/download.php](http://www.linuxpowertop.org/download.php)
[http://www.linux.com/article.pl?sid=07/05/16/1742204](http://www.linux.com/article.pl?sid=07/05/16/1742204)

So I installed it and ran it, this is what it says:
```

    PowerTOP version 1.2       (C) 2007 Intel Corporation                       

Cn          Avg residency (5s)  Long term residency avg
C0 (cpu running)        (100.0%)
C1                0.0ms ( 0.0%)                   0.0ms
C2                0.0ms ( 0.0%)                   0.0ms
C3                0.0ms ( 0.0%)                   0.0ms
C4                0.0ms ( 0.0%)                   0.0ms

No detailed statistics available; please enable the CONFIG_TIMER_STATS kernel option
This option is located in the Kernel Debugging section of menuconfig
(which is CONFIG_DEBUG_KERNEL=y in the config file)

Suggestion: Enable the CONFIG_NO_HZ kernel configuration option.
This option is required to get any kind of longer sleep times in the CPU.

```

Now the options they recommend enabling - will require a recompile of the kernel from source?
which means no auto updates ever in future...:( ???
Is there another way to do this?

Thanks guys

---

### Post by extremecarver on 2007-05-18
Yes you need to recompile the kernel for that, not that no-hz patch is only in 2.6.21 meaning that you probabely need that one - maybe its backported.
The second option can be found under kernel-debug but exists as well I think only .21 upwards, its not easy to find there however.

---

