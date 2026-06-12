---
title: "dbus-daemon - hogging cpu"
date: 2014-02-03
forum: General Help
---

### Post by snowguy on 2014-02-03
I installed 13.10 on my laptop about a week ago and every once in a while (i can't figure out what kicks it off) dbus-daemon takes over one of the CPUs. I can see this through the system monitor where it shows as a process consistently taking 24% of the cpu. When I look at the resources tab I can see one CPU is flat at 100%.

Any suggestions on how to trouble shoot this issue? 

I found this [related post]("http://ubuntuforums.org/showthread.php?t=1275316&highlight=dbus-daemon+-+hogging+cpu") but it didn't provide any answer.

If I go to the processes tab and click "stop process" on the process it fixes the immediate issue.

---

### Post by tim28 on 2014-04-01
This issue also affects me. Newish install of 13.10 (a week and a half ago?). Conky seems to think that the process is using 0.00 memory but maxing out a core of its own. No ideas, it looks like the only dbus.log I can find is unrelated (~/.cache/upstart/dbus.log seems to only mention a indicatior-application-service warning).

---

