---
title: "CPU throttling under low util when gaming; OK under 100% util when stress testing."
date: 2020-04-06
forum: General Help
---

### Post by sczvz on 2020-04-06
Hi all,

I am on Ubuntu 19.10 (fresh install) with laptop ASUS G501J and I experience heavy lag when starting games. I first noticed this with Divinity Original Sin 2 under Proton.
After some investigation I saw that my CPU ( Intel i7-4720HQ 2.6GHz) throttles down to ~ 200Mhz ( temps ~85C) in the character selection screen.

I limited the clock speed to ~1.6GHz with:
```
echo 40 | sudo tee /sys/devices/system/cpu/intel_pstate/max_perf_pct
```

And disabled turbo boost:
```
echo "1" | sudo tee /sys/devices/system/cpu/intel_pstate/no_turbo
```

Then I ran ```
stress --cpu 8 --io 4 --vm 4 --vm-bytes 128M --timeout 1000s
``` and the system was OK.
However, when running DOS2 the CPU still throttled (when utilization was 12%) in the character creation screen.

Here are the s-tui screenshots:
[https://imgur.com/a/feKq9h1](https://imgur.com/a/feKq9h1)

I am really confused. If any of you has an idea of whats going on please share.

Thanks,
sczvz

---

### Post by Impavidus on 2020-04-06
If the utilisation is only 12%, it's to be expected that the CPU trottles down. It seems to me that the CPU is not the bottleneck that causes your game to lag.

---

### Post by sczvz on 2020-04-06
Throttling to 200MHz is certainly not expected. I performed the tests several more times and found that the utilization does go up to 100%. 
The most probable cause is just overheating because I tried starting the game from a cold boot and then it doesn't lag for ~5 mins, but when the temp spikes and CPU throttles down, it starts.

---

