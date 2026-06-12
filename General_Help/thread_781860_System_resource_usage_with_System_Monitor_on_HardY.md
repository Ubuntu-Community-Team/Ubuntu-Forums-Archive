---
title: "System resource usage with System Monitor on HardY Heron"
date: 2008-05-04
forum: General Help
---

### Post by finite9 on 2008-05-04
when monitoring system resource usage with System Monitor on HardY Heron on Intel Core2 Duo 7200, CPU goes to 39% constantly (Xorg process).  And System Monitor shows that the 39% workload keeps switching between the 2 cores.  As soon as System Monitor is closed, the CPU drops to nearly zero percent usage again.  System Monitor does not report that the CPU is being used in the Processes tab at all.  I monitored CPU usage with Top.

sorry, don't know a workaround.  Maybe this is the wrong thread for posting an issue without a workaround?   Would be interested to know if anyone else has this issue though.

---

### Post by pPrdrm on 2008-05-15
This also happens to me too. But I think that it has to do only with the "Resourses Tab" of Sytem Monitor and not the whole app. If I switch to any other tab CPU usage is back to normal.

---

### Post by BlueSkyNIS on 2008-05-15
There is a known issue with the System Monitor, use TOP or alternative. I think fix for the System Monitor is in progress, check [https://bugs.launchpad.net/gnome-system-monitor/+bug/93847]("https://bugs.launchpad.net/gnome-system-monitor/+bug/93847")

---

### Post by finite9 on 2008-05-15
now fixed.  I had previously mailed the author and h said to try nv driver instead of nvidia-glx and that did make it drop to under 10%.  Now it's under 5% and smooth with the patch yesterday.

---

### Post by pPrdrm on 2008-05-15
Yes, but using the nv driver instead the nvidia one it means that you loose hardware acceleration. I realy like my compiz desktop to go back to nv driver :)

---

### Post by finite9 on 2008-05-16
you dont use a laptop then?  I can *see* my battery icon losing juice every few seconds with compiz enabled.

Yes it's pretty but does not add anything to useability.  I would use it is resource usage was anywhere near decent, but as it stands, it's not good for laptops.  using nv is even better for battery.

---

### Post by pPrdrm on 2008-05-16
It's not only for eye candy. If you don't use the proprietary drivers of nvidia you cannot use programs that need hardware acceleration (like blender or games etc.). Besides there was no problem with previous version of ubuntu. In general, for an LTS version, Hardy messed up a lot of things.

---

