---
title: "Time is not on my side (problems with ntp)"
date: 2007-11-19
forum: General Help
---

### Post by mmcmonster on 2007-11-19
I am running ntp to make sure my system clock doesn't drift much.  I forgot about it for a couple months, and now notice that the system clock is still 5 minutes off.

What am I missing?  My system is generally on 24 hours a day with infrequent reboots.

---

### Post by nick_h on 2007-11-19
You could have a look in /var/log/syslog.0 to check that it is running.

If it isn't right-click on the clock and select "Adjust Date & Time".  Then check that the syncronise option is selected and that you have selected a time server.

---

