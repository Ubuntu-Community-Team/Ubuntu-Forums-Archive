---
title: "Kalarm doesn't start"
date: 2008-04-10
forum: General Help
---

### Post by AdrianStrays on 2008-04-10
I installed Kalarm and set up various alarms, but I discovered upon reboot that although I have the "start on boot" option checked, it doesn't start on boot. Naturally, having to start up Kalarm everytime I need to be alerted about something kind of defeats the purpose of it.

Additionally, I have to run it from the terminal, and I get the following:

adrian@Alpha-60-Workstation:~$ /usr/bin/kalarm
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
kbuildsycoca running...
adrian@Alpha-60-Workstation:~$ 


Help?

---

### Post by opscure on 2008-04-10
Well there are a couple things you could do.  First, is KAlarm holding all your alarms and just not starting up or do you have to reconfigure it each time?  If it is just not starting up then you can add kalarm to the autostarted applications menu inside your applications->settings menu.  

An alternative is to use cron to play an audio file.  You can set up a script called alarm.sh with the following
```

#!/bin/sh
aplay ~/myalarm.wav &

```
and then use cron to schedule when you want this to be executed.  For example if you wanted this to go off 5 minutes after midnight you could edit your corntab file with this addition:
```

5 0 * * * /home/`whoami`/alarm.sh >/dev/null 2>&1

```

or you could remove the redirect (to dev null) at the end and add a MAILTO="you@youraddress.com" to receive an e-mail when the job is processed.

Hope this helps, and don't forget to man command for more information about a specific feature.

---

### Post by AdrianStrays on 2008-04-10
Kalarm has a record of all the alarms I've set.

I am not using KDE, I suspect that has something to do with it. 

I am not seeing the Settings option...

---

### Post by AdrianStrays on 2008-04-11
Bump

---

### Post by AdrianStrays on 2008-04-11
>: ( Bump

---

### Post by AdrianStrays on 2008-04-11
......Buuuummmppp..............

---

