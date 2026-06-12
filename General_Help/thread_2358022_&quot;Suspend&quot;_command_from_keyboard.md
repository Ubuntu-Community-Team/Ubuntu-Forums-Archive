---
title: "&quot;Suspend&quot; command from keyboard?"
date: 2017-04-08
forum: General Help
---

### Post by ra7411 on 2017-04-08
Ub 16.04.
Is there a keyboard combination that can cause the system to go into "suspend"?

Once in a while, on my desktop, I leave the monitor off when I "wakeup" the system, and then the monitor winds up not getting any signal, and I have to do a reboot to correct the situation. A keyboard command to return it to "suspend" then do another "wakeup" should solve the problem.

Thnx

---

### Post by TheFu on 2017-04-08
The command you want is **sudo /usr/sbin/pm-suspend**.
I made a setting inside the window manager settings to make that work. 
It is often common to connect the power button to it - /etc/systemd/logind.conf has specific settings for what causes what.
HandlePowerKey=suspend
HandleLidSwitch=suspend

Things like that.

---

