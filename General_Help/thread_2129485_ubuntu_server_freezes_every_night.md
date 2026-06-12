---
title: "ubuntu server freezes every night"
date: 2013-03-26
forum: General Help
---

### Post by psyncho on 2013-03-26
I've got a mystery on my hands. I've checked syslog and the only thing I see that is not hourly (it doesn't freeze hourly) is :
Mar 25 23:37:52 coeus dbus[448]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Mar 25 23:37:52 coeus dbus[448]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Mar 25 23:37:52 coeus polkitd[1826]: started daemon version 0.104 using authority implementation `local' version `0.104'
Mar 25 23:37:52 coeus dbus[448]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Mar 25 23:37:52 coeus dbus[448]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'

The weird thing - this is a server. There is no desktop. I don't remember installing anything like a desktop, use shell only. Maybe that's the problem. 

I've gone through /var/log looking for anything that has changed, but am not finding anything meaningful. Any tips on where to look next would be helpful. Also, any tips on what these log entries are about and if they might be related to the freezing would be appreciated. It's all I have to go on. 

thanks, 
John

---

### Post by HermanAB on 2013-03-26
Howdy,

Look in the root crontab and in /etc/cron.daily.  Disable everything and see if the machine keeps going.  If it does, devide and conquer.

---

### Post by psyncho on 2013-03-26
Thanks, yeah, obvious in hindsight.

---

