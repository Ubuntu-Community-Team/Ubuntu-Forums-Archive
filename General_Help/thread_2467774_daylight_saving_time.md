---
title: "daylight saving time"
date: 2021-10-07
forum: General Help
---

### Post by miha1234 on 2021-10-07
Hello

I have one question. I have set timezone to Europe/London. So when it comes daylight change time (31.10.2021 this year at 3 am) I would like that linux revert time to 2am (from 3 am) but instead the time stays the same, it just change time zone.

How to set date that it will show different time and not just different timezone.


thank you

---

### Post by Rex Bouwense on 2021-10-07
Under Settings>Date & Time, enable Automatic Date & Time (The first option).  This should then automatically change the time when Daylight Savings Time ends.

---

### Post by miha1234 on 2021-10-07
Hi @Rex. I mean in shell, not using graphicInterface.

timedatectl status
               Local time: Fri 2021-10-01 21:00:32 CEST
           Universal time: Fri 2021-10-01 19:00:32 UTC
                 RTC time: Fri 2021-10-01 19:00:34
                Time zone: Europe/Amsterdam (CEST, +0200)
System clock synchronized: no
              NTP service: n/a
          RTC in local TZ: no


Thank tou

---

### Post by grahammechanical on 2021-10-07
You should receive an update to a package called tzdata that controls the changes due to daylight saving time.

> graham@sdb1-sdb8:~$ timedatectl status
               Local time: Thu 2021-10-07 21:15:01 BST
           Universal time: Thu 2021-10-07 20:15:01 UTC
                 RTC time: Thu 2021-10-07 20:15:00    
                Time zone: Europe/London (BST, +0100) 
System clock synchronized: no                         
              NTP service: inactive                   
          RTC in local TZ: no

It is my understanding that the time change takes place on 31 October 2021 for both UK and EU.

> Clocks in most European countries are turned back by 1 hour on **October 31, 2021 at 01:00 UTC**.  Since Europe spans several time zones, the switch occurs at different  local times (see table below). DST in Europe starts again on Sunday,  March 27, 2022.

> Daylight saving time 2021 in United Kingdom began at 01:00 on Sunday,28 March and ends at 02:00 on Sunday, 31 October. All times are in United Kingdom Time

Quotes from an internet search.

Regards

---

### Post by ActionParsnip on 2021-10-07
I suggest you set an NTP source so that time is accurate

---

