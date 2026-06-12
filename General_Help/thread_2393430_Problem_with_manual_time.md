---
title: "Problem with manual time"
date: 2018-06-03
forum: General Help
---

### Post by wonder2 on 2018-06-03
Hello.
Recently, I installed Lubuntu 18.04 in my laptop, all fine but, when I go to set time (in mode manual) after 2 or 3 seconds, automatic sync the time and set the time, not my manual time.

Its possible edit this?

Thanks and regards.

---

### Post by TheFu on 2018-06-03
You'd need to disable all network time capabilities.  I don't use 18.04, but on prior releases it was based on NTP.

Might be easier just to change the timezone.

---

### Post by wonder2 on 2018-06-03
Hello.
No, I don't want change the timezone, only want change the time (a few minutes more).
In synaptic, I view that, I don't have installed any about NTP.

Thanks.

---

### Post by nlee2 on 2018-06-03
With Automatic Date and Time Setting = Off

What is the output of

systemctl status systemd-timesyncd.service

---

### Post by wonder2 on 2018-06-03
> **nlee2 said:**
> With Automatic Date and Time Setting = Off

What is the output of

systemctl status systemd-timesyncd.service
In system settings - date and time, unlock and set to Manual.

This is the output:

```
~$ systemctl status systemd-timesyncd.service&#9679; systemd-timesyncd.service - Network Time Synchronization
   Loaded: loaded (/lib/systemd/system/systemd-timesyncd.service; enabled; vendo
   Active: active (running) since Sun 2018-06-03 21:55:45 CEST; 1min 7s ago
     Docs: man:systemd-timesyncd.service(8)
 Main PID: 350 (systemd-timesyn)
   Status: "Synchronized to time server 91.189.94.4:123 (ntp.ubuntu.com)."
    Tasks: 2 (limit: 4625)
   CGroup: /system.slice/systemd-timesyncd.service
           &#9492;&#9472;350 /lib/systemd/systemd-timesyncd


jun 03 21:55:45 portatil systemd[1]: Starting Network Time Synchronizati
jun 03 21:55:45 portatil systemd[1]: Started Network Time Synchronizatio
jun 03 21:56:15 portatil systemd-timesyncd[350]: Synchronized to time se
```

Like indicate, in synaptic, I don't have installed NTP but in this output appears.....

Regards.

---

### Post by nlee2 on 2018-06-03
Turn off network time sync via terminal

systemctl stop systemd-timesyncd.service
systemctl disable systemd-timesyncd.service
systemctl status systemd-timesyncd.service

---

### Post by wonder2 on 2018-06-04
> **nlee2 said:**
> Turn off network time sync via terminal

systemctl stop systemd-timesyncd.service
systemctl disable systemd-timesyncd.service
systemctl status systemd-timesyncd.service
Thanks.
With this, I los shync in "Daylight Saving" when change time?

Thanks.

---

### Post by TheFu on 2018-06-04
Having the correct time is very important for many network things.  I'd expect other things to break if time is off more than 1 minute. Security protocols use time a bunch.

---

### Post by nlee2 on 2018-06-04
> **wonder2 said:**
> Thanks.
With this, I los shync in "Daylight Saving" when change time?

Thanks.

To test this on your computer

set the timezone
set the clock to minutes before daylight savings time change
observe

---

### Post by wonder2 on 2018-06-04
> **nlee2 said:**
> To test this on your computer

set the timezone
set the clock to minutes before daylight savings time change
observe
Yes, its good iddea.
I go to try :)

Thanks.

---

### Post by wonder2 on 2018-06-05
> **nlee2 said:**
> Turn off network time sync via terminal

systemctl stop systemd-timesyncd.service
systemctl disable systemd-timesyncd.service
systemctl status systemd-timesyncd.service
I try this, work fine, but when restart laptop, again, sync the time.
> **nlee2 said:**
> To test this on your computer

set the timezone
set the clock to minutes before daylight savings time change
observe
I test this, set the clock to minutes before daylight savings time change, but not change for daylight.

Thanks.

---

### Post by nlee2 on 2018-06-05
It is normal for system time to sync to a real time clock on reboot in manual time mode. 

What is your use case to adjust internet time?

On reboot,

what is the real time clock RTC time?

what is the output of

timedatectl
zdump -v /etc/localtime |grep 2018

---

