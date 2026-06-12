---
title: "Computer don't reboot or halt"
date: 2014-07-09
forum: General Help
---

### Post by yann7 on 2014-07-09
Hi all,
i'm working on a ubuntu 14.04 server with ssh on X display installer, but without desktop environnement (only a lightweight WM).
Since several days, i can't reboot computer, commands like ```
sudo reboot
``` or ```
sudo shutdown -r now
``` or ```
sudo shutdown -h now
``` don't work

The system shutdown services, the fall to ubuntu background with "waiting white points", but the computer doesn't shutdown or reboot. I must do it manually by pushing the power button (only one pression, i don't have to wait 5 seconds to force shutdown).

I have no logs in /var/log (syslog and others), so i can't identify where is the problem. The only suspicious log entry in sys log i can view is about rsyslog that exits with code 15 but i don't konw if it is really related ti my problem.

Note that i've also tried to change grub LINUX_COMMANDLINE with parameter "reboot=b" but no changes.

Can someone help me ?

Thank you

---

### Post by yann7 on 2014-07-10
Auto reply : I found the problem

I've setted up an upstart job for irtrans server (VF210) that doesn't start and at shutdown when the system wanted to shutdown service, the job do not respond and the system was waiting indefinitely.

Problem is solved.

---

