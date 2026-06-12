---
title: "rsnapshot help"
date: 2007-08-29
forum: General Help
---

### Post by madman100 on 2007-08-29
hi all need help to understand this ERROR: At least one interval must be set. rsnapshot can not continue
i have tried to set in but it hard when you  do not understand interval i have tried the rsnapshot configtest and that the error i get rsnapshot encountered an error! The program was invoked with these options:
/usr/bin/rsnapshot configtest 
----------------------------------------------------------------------------
ERROR: At least one interval must be set. rsnapshot can not continue.
eddie@eddie-desktop:~$ rsnapshot configtest

thanks :(

---

### Post by obrient on 2007-12-09
If you look at your config file you will see a section called interval. You need to take out the # from infront of one of those at least. So depending whether you want hourly, daily, weekly, or monthly backups depends on what you should set.

---

