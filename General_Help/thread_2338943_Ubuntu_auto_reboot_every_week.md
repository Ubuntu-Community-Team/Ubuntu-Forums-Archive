---
title: "Ubuntu auto reboot every week?"
date: 2016-10-03
forum: General Help
---

### Post by teslamodel on 2016-10-03
Hi,

I setup Ubuntu as kiosk and i want it to reboot every week to prevent some problems. How can i make it auto reboot every week at 00:00 (12 AM)?

---

### Post by TheFu on 2016-10-03
Use cron. [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

However, rebooting *just because* shouldn't be necessary. This isn't Windows.
If you patch weekly (and if it is on the internet, that would be recommended), then if a reboot it needed there will be a /var/run/reboot-required file. If it exists, then a reboot is needed.

---

