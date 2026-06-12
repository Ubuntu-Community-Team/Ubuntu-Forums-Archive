---
title: "CPU frequency scaling - Powersave"
date: 2008-06-15
forum: General Help
---

### Post by pb_online on 2008-06-15
I am using Kubuntu 8.04

I enabled cpu freq scaling and use the powersave governor because I have a laptop.
My processor is Core Duo 2.00 GHz

I noticed this...

Now, the two CPUs works on 250 MHz minimum and when needed go up.
I see my pc lag. For example, when I minimize/maximize firefox, it goes slow. Even if the processors go up.

On the other hand...

When I am on windows XP, The processors when I'm idle are 0% both but everything works fast. I never see lagging with XP.

I tried to set the minimum frequency at higher levels. I reached the 1.5GHz minimum but the issue it is. Only if I have the frequency on 2GHz, the lag does not exist.

:(

---

### Post by sdennie on 2008-06-15
The powersave governor locks the CPU at the lowest frequency (which generally makes things unpleasantly slow).  I *highly* recommend using the ondemand governor and not the powersave governor.  It turns out that ondemand is actually more efficient at power savings than powersave (google for "intel race to idle" for more information) and it's very hard to tell the difference between ondemand and performance for the majority of users.

---

### Post by pb_online on 2008-06-15
> **vor said:**
> The powersave governor locks the CPU at the lowest frequency (which generally makes things unpleasantly slow).  I *highly* recommend using the ondemand governor and not the powersave governor.  It turns out that ondemand is actually more efficient at power savings than powersave (google for "intel race to idle" for more information) and it's very hard to tell the difference between ondemand and performance for the majority of users.

My mistake...

I have it on "Dynamic". It is like "OnDemand".
There are three options... Performance, Dynamic, Powersave.

I am using KPowerSave

---

### Post by sdennie on 2008-06-15
So, you are saying that the output of:

```

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```

Is "ondemand"?

---

### Post by pb_online on 2008-06-15
Yes.

---

### Post by sdennie on 2008-06-15
Is it possible that this is a graphics card problem and not a frequency scaling problem?  What graphics card are you using?

---

### Post by pb_online on 2008-06-15
> **vor said:**
> Is it possible that this is a graphics card problem and not a frequency scaling problem?  What graphics card are you using?

Oh maybe it is that I set the ATI powerstate=1

But... On windows I have ATI on same powerstate.

Anyway, I will try set powerstate=3 and tell you.

---

### Post by pb_online on 2008-06-16
Ok i tried to set my graphics card powerstate to full and there is no any difference with Ondemand. My pc is slow, until I get it at 2GHz.

---

### Post by ravl on 2008-06-16
I'm using KPowersave with powernowd on my Turion64 x2 and it throttles the CPUs wonderfully. But when I had KPowersave with powersaved, I couldn't configure the profile and it seem to be running at a fixed freq.

---

### Post by sdennie on 2008-06-16
There was once a bug where my frequency scaling would get "stuck" at 800Mhz.  It's possible that you are seeing something like this.  The fix for me was to simply to toggle to governor:

```

sudo sh -c "echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor"
sudo sh -c "echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor"

```

---

### Post by pb_online on 2008-06-17
Mine, doesn't stuck. If I open a program gets up to full frequency.
The problem is that my pc is a little "lagged"

---

