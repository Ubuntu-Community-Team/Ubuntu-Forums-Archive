---
title: "log file cleanup needed"
date: 2013-12-18
forum: General Help
---

### Post by ELMIT on 2013-12-18
In my log file (syslog) I find every 3 second this entry:

kernel: [ 5066.686341] type=1400 audit(1387361102.088:1662): apparmor="STATUS" operation="profile_replace" parent=5543 profile="unconfined" name="/usr/sbin/mysqld" pid=5547 comm="apparmor_parser"

What is it? How can I fix it?

bye

Ronald

---

### Post by ajgreeny on 2013-12-18
Every three seconds of the whole session, or just several instances once per session?

Is the line for exactly the same executable (/usr/sbin/mysqld in your case shown) or is it different for each line?  I get a similar line in my syslog repeated a few times, but it is only once per session that those lines appear as far as I can see.

---

### Post by ELMIT on 2013-12-18
As said in my initial message EVERY 3 SECONDS THIS ENTRY

;-)

---

### Post by steeldriver on 2013-12-18
This maybe?

[https://help.ubuntu.com/community/AppArmor#apparmor_status_reports_processes_that_are_unconfined_but_have_a_profile_defined](https://help.ubuntu.com/community/AppArmor#apparmor_status_reports_processes_that_are_unconfined_but_have_a_profile_defined)

---

### Post by ELMIT on 2013-12-18
restart of the computer solved it (thanks steeldriver)

---

