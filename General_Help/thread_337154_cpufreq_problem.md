---
title: "cpufreq problem"
date: 2007-01-12
forum: General Help
---

### Post by MrPingu on 2007-01-12
cpufreq-selector
I have a laptop with centrino cpu.
I'm using ubuntu 6.10

I used
```
cpufreq-selector -f 1700000 -g userspace
```
1,70 GHz is the highest available freq.

After a while gaming with cedega, the cpufreq is set to 600 MHz without me touching the cpufreq. Because cedega doesn't support changing of cpufreq, it makes the game lag and impossible to play.

Is there anything I can do to _really_ force the cpufreq to 1,70 GHz?

- MrPingu

---

### Post by Paerez on 2007-01-12
Its actually that your laptop is getting too hot. It is not cpufreq or cedegas fault. Try putting a little something under the back of your laptop to lift the back off the ground.

I had this same issue with my laptop when I put it on my lap and play civ 4 :D

EDIT: another tip is that when it slows down, flip the laptop over and wait 2 mins (pause the game too), then it should be ok.

---

### Post by MrPingu on 2007-01-12
I might not like it, but thanks =)

---

### Post by komputes on 2008-02-21
Just a thought:

```
sudo apt-get install cpufreq-utils
# Install the Utils
cpufreq-info
# shows all possible modes for your CPU (look for performance or aggressive under governors)
sudo cpufreq-set -g performance
# In my case this sets CPU statically to MAX
```

---

