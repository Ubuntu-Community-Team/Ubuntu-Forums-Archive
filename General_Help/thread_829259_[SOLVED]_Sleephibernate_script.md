---
title: "[SOLVED] Sleep/hibernate script"
date: 2008-06-14
forum: General Help
---

### Post by MasterJS on 2008-06-14
I'm running a personal webserver and I've already set the BIOS to boot up on its own at a specific time. I'd like to know if there is a script or something that could be used to have the computer sleep or hibernate at a specific time of the day.

---

### Post by MasterJS on 2008-06-14
bump

---

### Post by mali2297 on 2008-06-14
You can use **cron** or **at** to execute **/etc/acpi/hibernate.sh** or **/etc/acpi/sleep.sh**.

For tutorials, see
[http://www.ibm.com/developerworks/library/l-job-scheduling.html](http://www.ibm.com/developerworks/library/l-job-scheduling.html)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto).

---

