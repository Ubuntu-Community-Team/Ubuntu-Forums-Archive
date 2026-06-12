---
title: "I have 2 questions."
date: 2023-09-07
forum: General Help
---

### Post by innobius on 2023-09-07
The first is sometimes I click more than once to open a file and get 2 open with portal dialog boxes. You cannot get rid of the second. I would like to know how to get rid of this without restarting my computer

second with the top command how would I view a process's disk usage and which disk it is currently using?

---

### Post by TheFu on 2023-09-07
> **innobius said:**
>  
second with the top command how would I view a process's disk usage and which disk it is currently using?

**top** doesn't have that capability. You'll need to use other tools. Disk usage isn't tied to any specific process. You can see which files a process has opened, however. Use **lsof** for that.  If the running process doesn't have a file open, but _you_ consider it to be part of the process, there's no way.

**glances** does have i/o and disk use stats, but not on a per-process basis. Still, it might be worth checking out.  glances runs is a larger-than-normal terminal, so if you normally have 8+ terminals tiled on your desktop, you'll probably want to have the one running glances use 25% of the screen, if not 50%.

---

### Post by Holger_Gehrke on 2023-09-07
TheFu is mostly correct, **but** if you look in the man-page for top - specifically section 6b - you can add 'inspect other output' items to your personal configuration of top which will be available after hitting 'Y'. One example the man page gives is how to create an entry for running 'lsof' on the currently selected process.

Holger

---

