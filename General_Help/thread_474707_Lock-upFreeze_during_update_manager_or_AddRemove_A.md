---
title: "Lock-up/Freeze during update manager or Add/Remove Applications"
date: 2007-06-15
forum: General Help
---

### Post by DaemonBreed on 2007-06-15
Most of the time when I attempt to install updates or Add an application, ubutu will lock up. It locks up shortly after I select install and enter my administrative password. The downloading packages window comes up, but only contains 2 gray boxes instead of downloading packages. I have to hard reset eerythime this happens.

I have checked the system log and think it may be a problem with my network card. I use DriverLoader from Linuxant (30-day free trial, almost up) because my card (Linksys WPC54G ver. 3)is not supported by ubuntu. Below is an exerpt from the system log file.

-----
Jun 15 10:14:32 tim-laptop NetworkManager: <information>^IUpdating allowed wireless network lists. 
Jun 15 10:14:32 tim-laptop NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Jun 15 10:17:01 tim-laptop /USR/SBIN/CRON[5669]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 15 10:33:57 tim-laptop -- MARK --
------

I tried to update at 10:14, and had to hard reset the computer after it froze, Thus "10:33" is my current session.

Thank you for reading, any help offered will be highly appreciated.

---

### Post by DaemonBreed on 2007-06-15
Anybody have any idea what could fix this?

---

