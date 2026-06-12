---
title: "Setting CPU profiles"
date: 2020-03-22
forum: General Help
---

### Post by u666sa on 2020-03-22
What's happening.  THere is this app called CoreCtrl, it sets CPU profile (performance, power saving, etc) and also AMD graphics profile.  I don't have AMD, I have NVIDIA.  So I'm wondering, should I be using it or is there something else I could use to set CPU profile?

---

### Post by CatKiller on 2020-03-22
It's not like you have an Nvidia CPU.

Personally, I just use ```
echo performance | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
``` but there are plenty of user-friendly tools to change the governor. That CoreCtrl is probably one, as is Feral's GameMode - which also sets some other things that are useful for gaming - or just the standard panel widgets.

For the GPU you'll want to set up CoolBits and then you can either use the normal Nvidia settings application, or script using the nvidia-settings command-line tool and nvidia-smi. For example, I use ```
sudo nvidia-smi --power-limit=350
``` to release the power limit on my GPU, and I have a script that overclocks it when I want to:

```
#!/bin/sh

nvidia-settings -a [GPU:0]/GPUMemoryTransferRateOffset[4]=1000
nvidia-settings -a [GPU:0]/GPUGraphicsClockOffset[4]=100
exit 0
```

There's GreenWithEnvy if you want a prettier method, but I've never tried it.

---

