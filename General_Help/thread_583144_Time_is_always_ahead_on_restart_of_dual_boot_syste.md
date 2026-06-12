---
title: "Time is **always** ahead on restart of dual boot system"
date: 2007-10-20
forum: General Help
---

### Post by genbie on 2007-10-20
Hi,

I have the time **_always_** ahead on a dual boot (Vista/Ubuntu) system. Every time I start Ubuntu I have to adjust the time! I tried most of the solutions on similar threads but none worked. I also tried this solution but it did not work! [http://ubuntuforums.org/showpost.php?p=698200&postcount=5](http://ubuntuforums.org/showpost.php?p=698200&postcount=5)

The output I get from 

> sudo /etc/init.d/hwclock.sh restart and hit [Enter]

is:

> * Saving the system clock
select() to /dev/rtc to wait for clock tick timed out


Any help is greatly appreciated.

---

### Post by Irony on 2007-10-20
From my notes;

[PHP]gksudo gedit /etc/default/rcS[/PHP]

Change;

[PHP]# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=yes[/PHP]

to;

[PHP]# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=no[/PHP]

Just seen that you said this didn't work - so I don't know the answer; perhaps check your BIOS.

---

