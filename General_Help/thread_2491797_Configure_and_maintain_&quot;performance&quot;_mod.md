---
title: "Configure and maintain &quot;performance&quot; mode"
date: 2023-10-20
forum: General Help
---

### Post by beirute2 on 2023-10-20
Hello Ubuntu Linux friends!


I like to use my computer at performance mode and I have used this command to put it in that mode:


[HTML]echo performance | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor performance[/HTML]

and check with:


[HTML]cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor powersave[/HTML]And it works as expected...


The problem is that every time I restart Ubuntu I have to do it again.


Does anyone know how to make it permanent?


Thank you!

---

### Post by MAFoElffen on 2023-10-22
First do
```

powerprofilesctl list

```
Check the output of that command first. It will list the "available" power profiles with their names and in that output, place an asterisk (*) in front of what the current setting is set to.

You set it by doing
```

powerprofilesctl set performance

```
To make that persistent, add that command as a startup app...

The reason I said to ensure it is available, is because I have one laptop that does not have performance (profile) as an option. I thought I could force a machine into a 'performance' profile mode, even though it was not listed as an option, just by setting it manually... It did set that, but... "*Just because something is possible doesn't make it a good idea.*"

What that did was to crash gnome-control-center (Ubuntu Settings) so that it would not start = just repeatedly crashed. It was because that power profile was set to an invalid option. It was set to performance, I could read the registers to verify that...
```

gdbus call --system --dest net.hadess.PowerProfiles --object-path /net/hadess/PowerProfiles --method org.freedesktop.DBus.Properties.Set 'net.hadess.PowerProfiles' 'ActiveProfile' "<'performance'>" | grep 'ActiveProfile ='

```
But the gnome-control-center could not handle the outside-the-box change. Resetting that option back, fixed gnome-control-center.

LOL. Lesson learned.

---

### Post by beirute2 on 2023-10-26
Thank you so much @MAFoElffen!

It was more than I asked LOL

RESOLVED :D

---

