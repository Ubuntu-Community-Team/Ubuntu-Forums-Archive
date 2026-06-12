---
title: "[SOLVED] Disabling startup daemon"
date: 2008-06-24
forum: General Help
---

### Post by Habbit on 2008-06-24
I'd like to know how could I disable a startup daemon, powernowd in particular, preferably without messing inside /etc/rcX.d or /etc/init.d. I've been to System->Administration->Services, and unchecked the box next to "CPU frequency manager (powernowd)", but the daemon keeps starting on boot and establishing the ondemand CPU frequency scaling governor. This is usually good, as it reduces power usage and thus heating, but this computer runs BOINC, and I want the CPU at full power. It seems that, as BOINC processes are niced, they using 100% CPU is not enough for the ondemand governor to switch to full-power mode. What can I do to exile powernowd to the abyss of unused programs? :confused:

---

### Post by x1a4 on 2008-06-24
```
sudo update-rc.d powernowd stop 90 1 2 3 4 5 6
```
will stop powernowd in position 90 on all run-levels

---

### Post by Habbit on 2008-06-24
That was not exactly what I wanted, but your post introduced update-rc.d to me, and I finally ran "update-rc.d -f powernowd remove", and same for powernowd.early. These commands which removed /etc/rcX.d links without deleting the /etc/init.d scripts, which I might someday need, so I'm happy. Thanks! :popcorn:

---

### Post by x1a4 on 2008-06-24
Glad I could help.  Be sure to mark the thread as solved.

---

