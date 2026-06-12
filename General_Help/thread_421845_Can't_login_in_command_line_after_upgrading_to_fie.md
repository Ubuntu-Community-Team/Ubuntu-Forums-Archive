---
title: "Can't login in command line after upgrading to fiesty"
date: 2007-04-24
forum: General Help
---

### Post by Rzulf on 2007-04-24
When I click "ctrl+alt+f1" (or any other f2,f3,f4...) there is no place to login. The last line is "Running local bootscripts (/etc/rc.local)      [OK]". On the other screens (f2,f3,f4) ther is only "_" blinking. I don't get what is wrong because command line is considered to be working even if other services fail (for example x.org) but on my PC everything works and login to console doesn't.:mad:

---

### Post by Rzulf on 2007-04-25
Ok, I solved the problem. I installed sysvinit and remove upstart, now it works like a charm, but what is the reason for this problem??

---

