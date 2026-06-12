---
title: "Very long restart/shutdown on 14.04"
date: 2014-04-19
forum: General Help
---

### Post by Cvetan on 2014-04-19
I did a fresh install of thrusty. The thing is that restart or shutdown takes very long time, 14, 15 seconds.

These are the specs of computer:
Asus P8B75-V with Intel B75 chipset,
Intel core-i5 2320 3GHz,
8GB RAM,
Asus Radeon EAH6450(HD 6450)

Has anyone had issue? Any advice?

---

### Post by david98 on 2014-04-19
I have not had that problem had trusty installed for about a month and a half and never came across that. Does it happen on every shutdown/restart ?

---

### Post by Cvetan on 2014-04-19
Yes. Every time, since i installed it.

---

### Post by david98 on 2014-04-19
Have you got any programs running in the background that may need to be closed before shutting down ?

---

### Post by Cvetan on 2014-04-19
No. I have the same setup that i always have with the Ubuntu. Not one release since now didn't have this issue.

---

### Post by david98 on 2014-04-19
Same here I have only ever had the problem your having in buntu 11.10 but that was a known bug. Am sorry I can't help you with this matter hopefuly someone with more knowledge will come and help shed some light on the problem. I hope you get it solved soon as I  guess it's quite annoying

---

### Post by Cvetan on 2014-04-19
It looks it is something related to ntfs partition for which i set options to be mounted at startup. I made those changes in disks application. 

When i returned to default options, shutdown-restart came back to normal. :confused:

---

### Post by Cvetan on 2014-04-21
The file system was set on auto in fstab. I've set it to ntfs-3g and it fixed the problem.

---

