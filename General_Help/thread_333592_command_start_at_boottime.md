---
title: "command start at boottime"
date: 2007-01-07
forum: General Help
---

### Post by ezazazel on 2007-01-07
I need to start this command at boot time:
sudo ./setpci -s 06:01.2 4c.b=0x02

It enables the Interrupt for the mmc reader.

how to do it? a file chmod +x in the init.d isn' t enough.

Plz help

---

### Post by Jussi Kukkonen on 2007-01-07
single line stuff should probably just go into /etc/rc.local (make it executable if it isn't already)

If you want to do it with init-scripts, init.d is where the script should be located, but you have to add symlinks to the script in /etc/rcX.d also (where X is the wanted runlevels). You can do that by hand, or with update-rc.d.

---

