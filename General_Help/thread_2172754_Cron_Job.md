---
title: "Cron Job"
date: 2013-09-06
forum: General Help
---

### Post by jeremy-lacey on 2013-09-06
Hello all I'm studying for the a+ Linux comptia exams need help with cron jobs please 
i typed 
Shell=/bin/bash
Mailto = username 
54 15 ***/sbin/ifconfig 

I've changed my username for my email address and typed crontab cronjob and all I get it bad hour or bad min ??

Any ideas why? 

Thanks for your time

---

### Post by bluefrog on 2013-09-06
what happens if you put spaces?
54 15 * * * /sbin/ifconfig

---

### Post by jeremy-lacey on 2013-09-07
tried that and still get bad day month. this is what is get on my screen

"cronjob":4: bad day-of-month
errors in crontab file, can't install.

---

### Post by ian-weisser on 2013-09-07
Do you understand what that error message is trying to tell you?
Hint: You made a syntax error. Syntax in a crontab, including spaces and the correct element in each column, is important.

---

