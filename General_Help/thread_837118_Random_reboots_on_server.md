---
title: "Random reboots on server"
date: 2008-06-22
forum: General Help
---

### Post by Xyem on 2008-06-22
This morning my server ( running 7.10 ) seems to have rebooted 4 times in the early morning when I was asleep.
I hadn't scheduled any reboots and I am the only one with root/sudo privileges.

I've checked the log files but nothing seems to show up to indicate a failure or anything.
The command 'last reboot' shows me the system has rebooted 4 times this morning:

> reboot   system boot  2.6.22-14-generi Sun Jun 22 10:37 - 12:01  (01:23)
reboot   system boot  2.6.22-14-generi Sun Jun 22 10:24 - 12:01  (01:37)
reboot   system boot  2.6.22-14-generi Sun Jun 22 09:15 - 12:01  (02:45)
reboot   system boot  2.6.22-14-generi Sun Jun 22 09:08 - 12:01  (02:52)

wtmp begins Thu Jun  5 08:43:55 2008


Can I check if a command did this? The only other explanation I can think of is there being power loss..

---

