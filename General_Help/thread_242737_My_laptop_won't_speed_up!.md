---
title: "My laptop won't speed up!"
date: 2006-08-24
forum: General Help
---

### Post by Rincebrain on 2006-08-24
So I've got a Pentium M 1.86 GHz in my Inspiron 9300. Ubuntu usually clocks the processor down to 800 MHz if I'm idling, which is perfectly fine.

When I'm trying to decode 1280x720 x264 and my processor is over 90% usage for half an hour and it decides that throttling the processor is a great idea, that's what I take an objection to.

I thought this could just be some odd setting, so I went looking for cpufreqd, the daemon I expected - nope, Ubuntu uses powernowd, which is reportedly supposed to clock it up selectively if your CPU is sitting at high usage for a reasonable period of time - oops. I went looking for a config file for powernowd, but I couldn't find one, and the man page didn't list any.

/etc/default/powernowd didn't exist, so the syntax for that was unknown to me, if it even read it at all.

I tried just stopping powernowd, and that worked fine - sometimes. But powernowd would mysteriously restart within the hour, which became increasingly annoying.

Then today, I started looking around in /sys/ for the appropriate settings to change my governor to something other than "userspace". I thought I had found what I was searching for in /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor, so I tried echoing "ondemand" (one of the choices from scaling_available_governors) to it, and read it back - success!

Sadly, the CPU didn't go anywhere above the minimum 800 Mhz, which worried me mildly. I tried setting other governors, including "performance", but none of them changed the speed at all, regardless of what demands I placed on the system.

I tried switching back to userspace, and then echoing my various speed options from scaling_available_frequences to scaling_setfreq, but despite never failing, none of these changed anything. I checked each time I did this to ensure that powernowd wasn't running and thwarting my efforts, and it was not.

I just want my laptop to run at a reasonable percentage of its maximum power when I want it to - IE: when I have it plugged into the wall for several hours watching various x264-encoded media streams. I can't remove powernowd, because A) that breaks ubuntu-desktop, and B) that still doesn't solve my confusion over why the CPU frequency didn't change after powernowd was dead and the governor was no longer userspace.

---

