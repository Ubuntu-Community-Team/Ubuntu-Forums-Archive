---
title: "Plans for a cpufrequtils settings panel?"
date: 2019-12-28
forum: General Help
---

### Post by dewdrop_world on 2019-12-28
Just wondering if there are rumors of any GUI forthcoming for cpufrequtils.

I just needed to set "performance" governing for a specific use case, and found:

   - sudo nano /etc/default/cpufrequtils
   - Write in this file: GOVERNOR="performance" or "powersave"
   - sudo systemctl restart cpufrequtils

But it's 2019 and we are editing configuration files for this? lol

Just curious. I'm OK to do it this way (and it does work) but wondering if anyone else thinks this is a bit oldschool.

hjh

---

### Post by CatKiller on 2019-12-28
The panel widgets can already set the governor, but the modern way to do it is with Feral's [gamemode](https://www.feralinteractive.com/en/news/966/) to automatically set the governor, and some other tweaks, just when you're playing a game.

If you want to set the governor manually from the command line you can you it with a single line:

```
echo performance | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```

---

