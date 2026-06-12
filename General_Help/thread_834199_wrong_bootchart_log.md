---
title: "wrong bootchart log"
date: 2008-06-19
forum: General Help
---

### Post by ziofil on 2008-06-19
hi everybody! 
i'm trying to have a better boot time, since I measured 82 secs to get to the login screen and 36 to the final desktop, for a total of almost 2 minutes... it's too long time.
so i installed bootchart.
It says that the total time to get to the login screen is 43 secs, but that is completely wrong! :confused:
how can I see exactly where all that time is lost?
in the end i have a medium computer: it's a laptop with 1Gb of ram, a pentium M 740 (1.73 Ghz) and 100Gb HDD...
any help is appreciated! :)

---

### Post by justleen on 2008-06-19
not sure, but i think you are measuring from power on, boot chats is measuring from init.. could that  account for 40 secs?

---

### Post by ziofil on 2008-06-19
i'm measuring from after the grub menu, i think bootchart does the same, doesn't it?

---

### Post by VMC on 2008-06-19
> **ziofil said:**
> i'm measuring from after the grub menu, i think bootchart does the same, doesn't it?

It appears that it starts during the init stage. This long boot time has come up before. There was a bootlogd program that worked in previous versions of ubuntu. Some have manage to hack up so it works in 8.04. Google "ubuntu bootlogd" and read up about it. Maybe you can vi /var/log/messages and find the START and then track back the times.

---

