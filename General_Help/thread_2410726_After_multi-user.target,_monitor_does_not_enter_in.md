---
title: "After multi-user.target, monitor does not enter in power saving mode."
date: 2019-01-19
forum: General Help
---

### Post by mr.sourcerer on 2019-01-19
So, without modifing default options of grub I have changed the system to "console" mode with the command "sudo systemctl set-default multi-user.target".
All fine, all working except of the monitor does not enter in power saving mode. Which is very annoying because the monitor is the second screen for my other system and when the other system starts power saving for monitors I lose the second screen because ubuntu's is always on.

I don't know what to modify or where to start from…

If I go back to gui with "sudo systemctl set-default grafical.target" or I start the gui with "sudo systemctl start gdm3.service" the monitor Works as normal and enters in powersaving mode…

Help, please

sourcerer

---

