---
title: "NTP updating with the wrong time"
date: 2013-06-27
forum: General Help
---

### Post by ricomoss on 2013-06-27
I've been trying to fix the clock on my laptop for a while now.  It appears to constantly keep updating to UTC rather than my local timezone (MDT).

The datetime config through the system settings shows MDT as my timezone.

```

ricomoss@soze:~$ ll /etc/localtime
lrwxrwxrwx 2 root root 18 Mar 14 10:46 /etc/localtime -> ../SystemV/MST7MDT

```

The system localtime is right.

If I stop the ntpd and force a manual update of the time it syncs with UTC.

```

ricomoss@soze:~$ sudo service ntp stop
 * Stopping NTP server ntpd                                                                                                [ OK ] 
ricomoss@soze:~$ sudo ntpdate ntp.ubuntu.com
27 Jun 23:12:42 ntpdate[2842]: adjust time server 91.189.89.199 offset 0.090691 sec
ricomoss@soze:~$ sudo service ntp start
 * Starting NTP server ntpd                                                                                                [ OK ] 

```

Any suggestions?

---

### Post by Sergius14 on 2013-06-27
Hi,

On Windows, you set time at BIOS in local time form. Then the OS has to be on your timezone. If you change your timezone you are in fact changing the BIOS time. Windows 8 allows you to use time in UTC (optionally) and since Vista SP2 you may use a registry hack to use time in UTC at BIOS.

On Linux (and any unix flavour) you have UTC or GMT0 time at BIOS and then the OS with the correct timezone will show up for the correct local time. Optionally, you may use local time instead of UTC (like Windows) at BIOS.


At this link is very well explained: [https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

---

