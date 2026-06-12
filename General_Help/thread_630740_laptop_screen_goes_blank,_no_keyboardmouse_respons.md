---
title: "laptop screen goes blank, no keyboard/mouse response"
date: 2007-12-03
forum: General Help
---

### Post by mjumbewu on 2007-12-03
Hi all,

I have a Toshiba Tecra M6 laptop with Gutsy (7.10) installed. Every so often, at irregular intervals (usually a few hours) the screen will go black (but not turn off, i.e. the backlight is still on) and the cpu fan will start to run high. What's more, it will not respond to any keyboard or mouse input -- no Ctrl+Alt+Del, no Ctrl+Alt+F1, no nothing.

A few things I've noticed: if I have video or music playing it will stop as well (though the last video frame will remain displayed on the screen -- i'm using Xv and compix+fusion); if the computer were simply idle, the media would keep going in the background. I've also looked at the messages log file, and the computer continues to post "-- MARK --" messages and run cron jobs.

Any ideas on how to fix or even debug this would be deeply appreciated.
Thank you,
- Mjumbe

---

### Post by metalheart on 2007-12-04
My first guess is power management problem. Disable all power management

```
/etc/init.d/acpid stop
```

and see if the problem still exists. Your laptops own power management may also have been set to aggressive (in BIOS).

---

### Post by mjumbewu on 2007-12-04
thanks for the reply.  since i have to wait a few hours to get this result, i will post how it works out in the morning.

---

### Post by mjumbewu on 2007-12-05
well, it hasn't happened for a couple of days, so i suppose it is something with acpi.

---

### Post by metalheart on 2007-12-05
Just monitor your computer, so it does not get too hot!

---

