---
title: "Incorrect Time in Lubuntu 16.04"
date: 2016-04-24
forum: General Help
---

### Post by Reetam on 2016-04-24
I have recently upgraded my Lubuntu to 16.04. And each time I restart it, it shows me incorrect time even if I have set it correctly prior to restart. I checked my BIOS time, it's fine so not an issue of BIOS time. Could someone please help me out with this?

---

### Post by Impavidus on 2016-04-24
Is the offset random or maybe an integer number of hours? That would indicate some kind of time zone confusion. Are you dual booting? The other OS might interfere.

---

### Post by Reetam on 2016-04-24
Yes, its setting the time back by 3 hours. I have Windows 7 as a dual boot. But this issue has started only after I upgraded my Lubuntu to 16.04. For the older version it was working fine.

---

### Post by vasa1 on 2016-04-24
Can you check if you have the *ntp* package installed? To do so, run *apt-cache policy ntp* in your terminal:
```
05:20 AM ~ $ apt-cache policy ntp
ntp:
  Installed: 1:4.2.8p4+dfsg-3ubuntu5
  Candidate: 1:4.2.8p4+dfsg-3ubuntu5
  Version table:
 *** 1:4.2.8p4+dfsg-3ubuntu5 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
05:20 AM ~ $ 
```

Also, what does *timedatectl | grep local* show?```
05:20 AM ~ $ timedatectl | grep local
 RTC in local TZ: yes
Warning: The system is configured to read the RTC time in the local time zone.
         'timedatectl set-local-rtc 0'.
05:26 AM ~ $ 
```For more on *timedatectl*, see [https://www.freedesktop.org/software/systemd/man/timedatectl.html](https://www.freedesktop.org/software/systemd/man/timedatectl.html)

---

### Post by Impavidus on 2016-04-25
The bios clock can be set to either local time or UTC. Windows likes it on local time. Keeping it on UTC is better when dual booting, as it is hard for one system to guess whether the other system has already applied daylight saving time (DST) or was changed from one time zone to another. Windows wasn't designed for dual booting.

Linux normally sets the bios clock to UTC, but can be configured to set it to local time. Maybe that configuration was somehow lost during the upgrade. If Windows sets the clock to local time, Lubuntu assumes it's set to UTC and you live in time zone UTC-3 (or UTC-4 with DST), the clock will run 3 hours behind.

You may be able to fix it by editing the file **/etc/default/rcS**. Open it in a text editor with root permissions, change the line **UTC=yes** to **UTC=no**, save and exit. But maybe vasa1 knows a better way to fix it.

---

### Post by vasa1 on 2016-04-25
> **Impavidus said:**
> ...
Linux normally sets the bios clock to UTC, but can be configured to set it to local time. Maybe that configuration was somehow lost during the upgrade. If Windows sets the clock to local time, Lubuntu assumes it's set to UTC and you live in time zone UTC-3 (or UTC-4 with DST), the clock will run 3 hours behind.

You may be able to fix it by editing the file **/etc/default/rcS**. Open it in a text editor with root permissions, change the line **UTC=yes** to **UTC=no**, save and exit. But maybe vasa1 knows a better way to fix it.
Sadly, I don't (and I don't have the problem either, even though I have a dual boot).

But, on reading around, I got the impression that rcS is no longer used in default 16.04 as a result of the switch to systemd.

This is my /etc/default/rcS:```
#
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
**# This file belongs to the "initscripts" package.**
# delete files in /tmp during boot older than x days.
# '0' means always, -1 or 'infinite' disables the feature
#TMPTIME=0

# spawn sulogin during boot, continue normal boot if not used in 30 seconds
#SULOGIN=no

# do not allow users to log in until the boot has completed
#DELAYLOGIN=no

# be more verbose during the boot process
#VERBOSE=no

# automatically repair filesystems with inconsistencies during boot
#FSCKFIX=no

```Every line is commented out. I bolded one particular comment.

---

### Post by Impavidus on 2016-04-25
> **vasa1 said:**
> 
But, on reading around, I got the impression that rcS is no longer used in default 16.04 as a result of the switch to systemd.


Well, that may explain why this problem occured after upgrading to 16.04. I'm still on 15.10 (and not dual booting). I don't know where this setting is stored now. Maybe someone will pop in with advice, or OP may find it using this lead.

---

### Post by vasa1 on 2016-04-25
@impavidus, please see [http://ubuntuforums.org/showthread.php?t=2321876&p=13476883#post13476883](http://ubuntuforums.org/showthread.php?t=2321876&p=13476883#post13476883)

---

