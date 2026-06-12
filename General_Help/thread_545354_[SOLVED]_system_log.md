---
title: "[SOLVED] system log"
date: 2007-09-07
forum: General Help
---

### Post by yorkie on 2007-09-07
Hi 
I have been running ubuntu 7.04 since it came out despite system freezes I think its great just encounted new problem,
when trying to display system logs system> administration > system log, blank window opens then dissapears. Any one got any ideas.
thanks

---

### Post by reckless2k2 on 2007-09-07
try running it from the terminal and post the error. throw gksudo in front and then see if you have the same problem.

---

### Post by yorkie on 2007-09-07
thanks for reply I have tried different commands in terminal but got nothing which command should I be using

---

### Post by yorkie on 2007-09-07
o`k did some digging had a look in /var/log noticed logs have not been updated had a look in system> administration> services and found that
 anacron was disabled so enabled it now o`k marked as solved

---

