---
title: "How to change default powernowd governor"
date: 2007-02-08
forum: General Help
---

### Post by noxxle on 2007-02-08
I want my laptop to use the Conservative governor when it is running on AC instead of OnDemand. How can i change this? I have run the chmod a+x command to enable users to change the powernowd settings, but i would prefer it does this automatically on boot.

---

### Post by dannyboy79 on 2007-02-08
didi you check this out?

[http://swem.wm.edu/blogs/waynegraham/index.cfm/2006/8/17/Improving-Ubuntu-GUI-Resposiveness](http://swem.wm.edu/blogs/waynegraham/index.cfm/2006/8/17/Improving-Ubuntu-GUI-Resposiveness)

i also found this in gogle:
to keep the machine running on lower noise as used from os x, read the powernowd manual (`man powernowd`) and adjust your local settings in /etc/defaults/powernowd. (for example: OPTIONS="-m 3 -u 95 -l 50 -p 3000 -q") 
also have a look at the files in /sys/devices/temperatures/* (they tell you some temperatures and fanspeeds), which are controlled by the module "therm_adt746x" (this is loaded in /etc/modules.conf - check `modinfo therm_adt746x` to adjust some settings, i use 'therm_adt746x limit_adjust=5 fan_speed=32' in /etc/modules).
good luck & noiseless computing,
;-)
solidether

---

### Post by noxxle on 2007-02-10
i dont have a /etc/defaults/powernowd directory

---

