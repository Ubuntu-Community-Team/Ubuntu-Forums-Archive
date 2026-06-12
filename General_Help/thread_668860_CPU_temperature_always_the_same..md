---
title: "CPU temperature always the same."
date: 2008-01-15
forum: General Help
---

### Post by FuturePilot on 2008-01-15
My CPU temperature is always reported as 40°C. It never changes, ever. I know this is incorrect because I can go into my BIOS and see the correct temp and it's nowhere near 40°C. Is there any way to fix this?

---

### Post by articpenguin on 2008-01-15
did you try 

> acpi -t

in the terminal?

---

### Post by FuturePilot on 2008-01-15
Yep, it's always the same
```
 Thermal 1: ok, 40.0 degrees C
```

---

### Post by articpenguin on 2008-01-15
what processor do you have

---

### Post by FuturePilot on 2008-01-15
That might help, should have put it in the first post. ;)
Intel Pentium 4 HT @ 3.4 GHz

---

### Post by articpenguin on 2008-01-15
this happed to my old Pentium 4 2.8Ghz  too stuck but only it was stuck at 35C all the time.

---

### Post by FuturePilot on 2008-01-15
Hmm. Interesting. Looks like it might be a thing with Intel Pentium 4s.
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/180658]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/180658")
Though my laptop has a Pentium 4 in it and it reports the temp fine.
Thanks for your help by the way. :)

---

### Post by warrior24 on 2008-01-15
same here but with an AMD 2600
 Thermal 1: ok, 40.0 degrees C

---

### Post by 3rdalbum on 2008-01-16
What are you using to report the CPU temperature?

If it's NOT "sensors", then install it. The first time you run it, it will detect what sensor modules it needs to load. From then on, it reports all the sensors.

Mine is quite wildly wrong unfortunately - the CPU fan speed is correct and I believe the CPU temperature readings are also correct, but it's reporting ridiculously high voltages on the motherboard. Oh well, it's useful to know when to turn on the air conditioning :-)

---

### Post by FuturePilot on 2008-01-16
Well I'm using acpitemp in Conky which reports the same thing that acpi -t does from the terminal.
I wouldn't think I would need to install anything since my other computers can report this info correctly without additional programs.

---

