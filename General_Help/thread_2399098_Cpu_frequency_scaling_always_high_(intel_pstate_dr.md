---
title: "Cpu frequency scaling always high (intel_pstate driver)"
date: 2018-08-21
forum: General Help
---

### Post by nacholucia on 2018-08-21
Hello, I've installed Ubuntu 18.04 in a Skylake i7 laptop, and i'm having a problem with cpu freq scaling.
I come from Arch linux, and the cpu scaled correctly between 800 - 3500 mhz. In Ubuntu, even when idle, the frequency is always > 3000 mhz.

If i run cpufreq-info i get the following:

```

analyzing CPU 0:
  driver: intel_pstate
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 4294.55 ms.
  hardware limits: 800 MHz - 3.50 GHz
  available cpufreq governors: performance, powersave
  current policy: **frequency should be within 3.50 GHz and 3.50 GHz.**
                  The governor "powersave" may decide which speed to use
                  within this range.
  current CPU frequency is 3.13GHz.

```


Any idea how can i set the minimum frequency to 800Mhz? I tried ```
cpufreq-set -d 800000

```,but it has no effect.

Thank you.

[edit]

I'm sorry to have bothered you, using cpupower worked 
```
cpupower frequency-set -d 800000
```

---

