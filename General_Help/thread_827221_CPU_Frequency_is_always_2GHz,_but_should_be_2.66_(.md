---
title: "CPU Frequency is always 2GHz, but should be 2.66 (e6750 C2D)"
date: 2008-06-12
forum: General Help
---

### Post by Repgahroll on 2008-06-12
Hello there :)

I have a e6750 processor and im rendering some animations but the CPU frequency is always 2GHz...

In Gutsy the processor always was 100% @ 2.66GHz, but now in hardy the processor is 90-99% @ 2Ghz

i tried:

x@y-desktop:~$ cd /sys/devices/system/cpu/cpu0/cpufreq
x@y-desktop:/sys/devices/system/cpu/cpu0/cpufreq$ sudo echo 'performance' >scaling_governor
bash: scaling_governor: Permission denied

but as u can see i get an error... i dunno what to do, i need the full power to render faster... :( :( :(

thanks

---

### Post by sdennie on 2008-06-12
Try:

```

sudo sh -c "echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor"

```

---

### Post by Repgahroll on 2008-06-12
> **vor said:**
> Try:

```

sudo sh -c "echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor"

```

sh: cannot create /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor: Directory nonexistent

Thank you very much!

But i ran the command on the first post logged as root (using su) and worked fine after reboot!

Now the frequency is stuck @ 2.67MHz in both cores and the rendering is using 100% of the processors :)

---

### Post by sdennie on 2008-06-12
For future reference, my guess is that the reason the CPU wasn't scaling all the way up is because your animations are started with "nice".  Applications that are niced aren't considered in the algorithm that determines what speed the CPU should run.

---

### Post by Repgahroll on 2008-06-12
> **vor said:**
> For future reference, my guess is that the reason the CPU wasn't scaling all the way up is because your animations are started with "nice".  Applications that are niced aren't considered in the algorithm that determines what speed the CPU should run.

Could be... but not in this case!

The cpu scaling was on demand, but even if i was openning a application like openoffice the frequency was stuck @ 2GHz... no matter what i did... i could open lots of programs at the same time and the frequency was always 2GHz... i think is something related to the power manager...a bug maybe? dunno :confused:

---

### Post by sdennie on 2008-06-12
It's possible that it's a bug as well.  There was a bug (maybe still is) where my CPU would get stuck at 800Mhz while set to ondemand.  The workaround was simply to set it to userspace and then back to ondemand and it started scaling again properly.  (This usually happened after suspend/resume)

---

### Post by Repgahroll on 2008-06-12
> **vor said:**
> It's possible that it's a bug as well.  There was a bug (maybe still is) where my CPU would get stuck at 800Mhz while set to ondemand.  The workaround was simply to set it to userspace and then back to ondemand and it started scaling again properly.  (This usually happened after suspend/resume)

:)

no matter to me now!:guitar: i never hibernate os suspend my computah

Thank you very much! :popcorn:

---

