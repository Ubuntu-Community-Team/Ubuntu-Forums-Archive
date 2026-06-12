---
title: "Webmin reboot cron job intermittently causes Ubuntu server to endlessly reboot"
date: 2016-11-30
forum: General Help
---

### Post by torbuck on 2016-11-30
Greetings

I have a Ubuntu 14.04.2 server, mainly used as a media server. I was having an issue a while back where the server would occasionally freeze. I band aided the situation by creating a scheduled reboot cron job 
using Webmin (/sbin/reboot). For the last few months, I've noticed that the server was unavailable again, but have now determined that the server gets in an endless reboot loop. It seems to occur after the
scheduled reboot. If I perform a manual reboot using webmin, the server reboots fine. However once a week or maybe every second week, I have this issue where the server is caught in this endless reboot.

I'm quite new to Linux so pretty green in terms of troubleshooting this. Any pointers on how I could prevent this from happening would be great.

Thanks,

Torbuck

---

### Post by TheFu on 2016-11-30
Look in the log files. They are usually pretty clear at pointing out issues.

Can't help with anything related to webmin. Never use it.

---

