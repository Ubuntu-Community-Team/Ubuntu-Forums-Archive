---
title: "How to check for systems shutdown/startup in 12.10?"
date: 2013-02-13
forum: General Help
---

### Post by Balthier1979 on 2013-02-13
Hello guys,
 
I am running the following commands every evening, using crontab
 
30 23 * * * root rtcwake -m mem -s 23000
15 6 * * * root reboot
 
I can see from /var/log/auth.log, that something has happened at those times (session closed/session opened), but I can also see the same type of messages at other times, when I know I haven't restarted the computer.
 
Is there any way I can check just the shutdowns and startups of the computer?
If I check in /var/log/boot.log, I can see some things being started and stopped, but there are no dates and times for when this is occuring.

---

### Post by schragge on 2013-02-13
This will show all reboots since */var/log/wtmp* was created
```

last reboot

```

---

### Post by matt_symes on 2013-02-13
Hi
 
Use the command.
 
```
 
last

```
 
That will show when users logged in and the machine was rebooted.
 
You can also check /var/log/syslog.
 
Kind regards

---

### Post by Balthier1979 on 2013-02-13
Thanks guys. :)

---

