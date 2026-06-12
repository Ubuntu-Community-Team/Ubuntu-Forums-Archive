---
title: "[SOLVED] CPU Underclocking"
date: 2008-06-19
forum: General Help
---

### Post by Zeotronic on 2008-06-19
Recently I have become interested in underclocking my CPU when it's full processing power is not needed... I read the [Underclocking article]("http://en.wikipedia.org/wiki/Underclocking") on Wikipedia trying to gain a better insight into how this works, and there I learned about cpufreq. Now my question is **how do I go about accessing cpufreq?** For those of you who use Xubuntu the CPU Frequency Monitor, and the Governor Plugin don't seem to do anything, and CPUFreq (all of those being panel items mind you) tells me 'CPUFreq support is not present. The CPUFreq Monitor will not function this session.'. Other efforts to check cpufreq, such as through cpufreq-info suggest that it is not running.

---

### Post by sdennie on 2008-06-19
Are you trying to do this to save battery power?  If so, you will actually do the reverse.  Letting the CPU switch between min and max power (so, the ondemand governor) actually saves more power on most CPUs than pegging it to minimum.  Google for "intel race to idle" for more information on why this is true.

---

### Post by Zeotronic on 2008-06-19
> Are you trying to do this to save battery power? If so, you will actually do the reverse. Letting the CPU switch between min and max power (so, the ondemand governor) actually saves more power on most CPUs than pegging it to minimum. Google for "intel race to idle" for more information on why this is true.
I know this, I know this... I don't want to use the minimum, I just want to make sure that it *is* set to ondemand... but I have not been able to figure out how to do this... which is why I'm here.

---

### Post by sdennie on 2008-06-19
Try:

```

sudo apt-get install cpufrequtils

```

To see what the current policy is:

```

cpufreq-info

```

To change it, check the man page for cpufreq-selector:

```

man cpufreq-selector

```

---

