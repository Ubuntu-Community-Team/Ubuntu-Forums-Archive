---
title: "Xubuntu: Get out of my session alone"
date: 2015-12-12
forum: General Help
---

### Post by abbobba2 on 2015-12-12
Hi! 
I recently install a ssd so I reinstall xubuntu 15.10.
But sometimes it  get out of my session and close every applications. Before installing ssd I didn't see this problem.

---

### Post by coffeecat on 2015-12-12
Xubuntu is an official flavour of Ubuntu, so moved from the Ubuntu/Debian Based sub-forum of the Other Operating Systems section to ***General Help**.*

---

### Post by grahammechanical on 2015-12-12
If the machine is shutting down and/or restarting, then it could indicate that when you installed the SSD you disturbed something else. Are all the fans working? Are the RAM chips attached properly. Is the machine overheating? Are the power cables attached properly?

---

### Post by abbobba2 on 2015-12-12
The machine isn't restarting, it simply exit from the current session so I have to re-login

---

### Post by ian-weisser on 2015-12-13
Look for crash reports in /var/crash
Look for error messages around the appropriate time in /var/log/Xorg.0.log and /var/log/syslog

---

