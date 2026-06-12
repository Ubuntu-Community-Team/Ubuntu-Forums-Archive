---
title: "CPU governor being reset from userspace to ondemand?"
date: 2012-10-18
forum: General Help
---

### Post by OneOfMany07 on 2012-10-18
We're trying to force our CPU to run at a specific speed during benchmarks, but some systems seem to reset their governor from "userspace" to "ondemand" after a short while (2-3 hours this most recent time between setting and noticing it changed).  Which basically invalidates our tests.

Any ideas what could be causing this?  Is there a tool running in the background that could be setting this again?  "ondemand" is our boot up default, which I'm considering changing after a few related Google searches.

To change the governor we've been doing something like...
```
sudo sh -c "echo 'userspace' > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor"
```
Yes I've seen cpufreqset in my searches, but we already have bash scripts to do this.

---

### Post by Lisiano on 2012-10-18
I don't remember anything trying to change my governor when I was forcing to userspace. You might try setting the scaling_governor to be read-only.
```
sudo chmod 444 /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```
Also you may use 'tee' to write to root files. Like this
```
echo 'userspace' | sudo tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

OR you could just set scaling_min_freq to be the same as scaling_max_freq, effectively forcing userspace mode for every governor, since they won't be able to scale bellow or past those limits.

---

### Post by wheeze on 2012-10-18
Ubuntu has a service that starts on boot called "ondemand" that seems to force that CPU governor setting (from what little I've experimented with it). If you disable that you should be able to control CPU speeds manually. I disable this and use cpufrequtils instead.

I'm using a MATE version of 12.10 so I don't know if you have a startup Services applet, but this is what it looks like in MATE.

BUM (bootup manager) might be able to do this as well.

---

### Post by OneOfMany07 on 2012-10-18
Both good ideas, thanks!

---

### Post by pqwoerituytrueiwoq on 2012-10-18
when the system boots it boots in performance mode later this script changes it to ondemand
/etc/init.d/ondemand
you want to edit line 27
and maybe be add a line to set the core speed for userspace

---

### Post by OneOfMany07 on 2012-10-19
I ended up changing the boot up value as suggested in /etc/init.d/ondemand to userspace, and I'm hoping that was the process that kept resetting me to ondemand (maybe the service was being triggered again?).  I still need to do some testing though.

Also updated ours scripts to show both expected and actual CPU speeds, along with what governor was running.  I only noticed this when I tried to set the speed and it failed because it wasn't userspace.  Hopefully it'll be more obvious now.

Thanks again all.

---

### Post by Doug S on 2012-10-19
After the 1 minute that the ondemand startup script delays before setting on demand mode, I have never seen anything else change the settings without specifically being asked to (I'm referring to desktop server computers. Laptops switch governors between battery mode and plugged in mode).
Perhaps you might want to review [this thread]("http://ubuntuforums.org/showthread.php?t=2063004").
Please let us know how you make out with your tests.

---

### Post by 2F4U on 2012-10-20
Another way to disable the ondemand scheduler:

```
sudo update-rc.d -f ondemand remove         
```

If you wish to re-enable it:

```
sudo update-rc.d ondemand defaults         
```

---

### Post by OneOfMany07 on 2012-10-24
Thanks Doug S for the link.  Yep, that gave me some other ideas for working around this issue (use a different governor), but in the end it feels like something is broken.  I shouldn't have to set max and min frequency to a single value to force my CPU speed.

On most systems we have userspace governor seems to work.  We have a decent range of CPU's, but basically one of each type.  The two that have changed the most on us are a Llano (AMD A8-3850) and an Android phone.  I figured the first would be easier to find support for with other people more likely using them in the same way.  But we have other AMD, and Intel systems that work as expected.

And yes, disabling the service is another idea.  For now I just left it at userspace and I didn't notice any resetting, but I never did find a good test case.  In the past it seemed to reset after a few hours of sitting there, but that isn't very scientific.  I'll poke at it through the day some more to see how it is fairing.

---

