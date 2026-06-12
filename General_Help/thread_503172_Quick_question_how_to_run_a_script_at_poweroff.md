---
title: "Quick question: how to run a script at poweroff?"
date: 2007-07-17
forum: General Help
---

### Post by T0MA on 2007-07-17
Ok, so I have a little script (basically one line) that I want to run when I restart or power off my computer... how can I do that?

thx!

---

### Post by po0f on 2007-07-17
T0MA,

Create an init script in /etc/init.d and set the script to run at levels 0 and 6 (shutdown and reboot, respectively).

---

### Post by T0MA on 2007-07-18
well, i put the script at init.d and used the following to run it at level 0 and 6:
sudo update-rc.d xp_savestate start 5 0 6 .

when i press restart it says:

/etc/init.d/rc: 2 /etc/rc6.d/S01cpkernel: Input/output error

and a couple of other lines like that and stops

what I'm trying to do is that if I restart my computer it would automatically save the state of the virtual machine running in virtualbox..

---

