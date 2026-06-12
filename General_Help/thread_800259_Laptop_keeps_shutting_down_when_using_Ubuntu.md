---
title: "Laptop keeps shutting down when using Ubuntu"
date: 2008-05-19
forum: General Help
---

### Post by NeonBible on 2008-05-19
Its fine for Windows XP, Xubuntu and Puppy Linux.  But with Ubuntu, after about 3 minutes it will shut down.

Is it overheating? I thought Ubuntus requirements arent particularly high?

Its a Celeron 900mhz with 384RAM, so its fairly old.

EDIT: damn, posted in the wrong forum! Was supposed to go in the beginners forum.  Can I move it?

---

### Post by amingv on 2008-05-19
You can't move your posts/threads, but if you make a mistake you can report your own thread and ask a mod/admin to move it to the right forum (already did so).

Puppy and Xubuntu are much lighter than Ubuntu, but I believe that if it was an overheating problem they would shut off eventually, too.
Any chance you can get to the BIOS after it shuts down and check the temperature? Are you overclocking?

---

### Post by Lux Perpetua on 2008-05-20
I use emifreq-applet to keep tabs on my cpu's temperature. 

Alternatively, get to know the /proc filesystem. On my machine, **cat /proc/acpi/thermal_zone/THM0/temperature** will show the temperature.

---

### Post by tseliot on 2008-05-20
Moved to a more appropriate section.

---

### Post by NeonBible on 2008-05-20
I'm not sure if the laptop even has Temp monitor capabilities!

---

