---
title: "Superblock last mount time is in the future..."
date: 2017-08-16
forum: General Help
---

### Post by Kris_M on 2017-08-16
How would I correct this?

i believe this happened at some point when I was upgrading from 16.04.3 to 17.4 . Using Gnome (3.24.2).

Otherwise, boots fine. Runs fine.

BIOS, Ubuntu/Gnome, win7 clocks are all the same.

In Ubuntu, hwclock is about 5 sec behind what Gnome displays in the top bar. Done when changed to 20:06
```
kris@kris-Z97X-UD3H:~$ sudo hwclock
2017-08-16 20:05:55.640108-0400
kris@kris-Z97X-UD3H:~$ 
```


hwclock -s doesn't fix it.

sudo ntpdate pool.ntp.org doesn't fix it.

   timedatectl set-local-rtc 1 doesn't fix it.

---

### Post by VMC on 2017-08-16
What's the output of this 'timedatectl'?
Also, it may be defective RTC clock or battery needs replacement.

---

### Post by Kris_M on 2017-08-16
Thanks.
```
kris@kris-Z97X-UD3H:~$ timedatectl
      Local time: Wed 2017-08-16 22:04:08 EDT
  Universal time: Thu 2017-08-17 02:04:08 UTC
        RTC time: Wed 2017-08-16 22:04:09
       Time zone: America/New_York (EDT, -0400)
 Network time on: yes
NTP synchronized: no
 RTC in local TZ: yes

Warning: The system is configured to read the RTC time in the local time zone.
         This mode can not be fully supported. It will create various problems
         with time zone changes and daylight saving time adjustments. The RTC
         time is never updated, it relies on external facilities to maintain it.
         If at all possible, use RTC in UTC by calling
         'timedatectl set-local-rtc 0'.
kris@kris-Z97X-UD3H:~$ 

```

---

### Post by Kris_M on 2017-08-16
yeah, it's all windows fault - it can't cope with a UTC bios clock.  I believe I can adjust by telling win not to access network clock set thing.

ran
timedatectl set-local-rtc 0

edit yeah I had to add 1 line to win registry to fix the problem. now bios is UTC and both Ubuntu and win7 show EST. and no superblock msg.
```
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\TimeZoneInformation] 
"RealTimeIsUniversal"=dword:00000001
```

THANKS!

---

### Post by VMC on 2017-08-17
I kept having the same issue until I fixed Windows. For Windows 10 64-bit:
```
[COLOR=#333333][FONT=Monaco]Reg add HKLM\SYSTEM\CurrentControlSet\Control\TimeZoneInformation /v RealTimeIsUniversal /t REG_QWORD /d 1[/FONT][/COLOR]
```

Then ubuntu:
```
timedatectl set-local-rtc 0
```

---

### Post by jerrynphoenix on 2018-06-20
> **VMC said:**
> I kept having the same issue until I fixed Windows. For Windows 10 64-bit:
```
[COLOR=#333333][FONT=Monaco]Reg add HKLM\SYSTEM\CurrentControlSet\Control\TimeZoneInformation /v RealTimeIsUniversal /t REG_QWORD /d 1[/FONT][/COLOR]
```

Then ubuntu:
```
timedatectl set-local-rtc 0
```


Awesome VMC!  I have been beating my head against the wall trying to figure this out all afternoon.   Nothing I found on the web helped until I read your post.    Your two steps fixed this issue in less than five minutes!  Thanks!

---

