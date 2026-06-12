---
title: "How to set time zone to UTC-5"
date: 2021-12-21
forum: General Help
---

### Post by tc2020 on 2021-12-21
Hello,

I would like to set time zone to UTC-5 in Ubuntu 20.04. The option list-timezones does not contain UTC but only Etc/GMT. If I select Etc/GMT-5, the time is wrong but Etc/GMT+5 gives correct time.

```
$ timedatectl
               Local time: Tue 2021-12-21 10:40:23 +05
           Universal time: Tue 2021-12-21 05:40:23 UTC
                 RTC time: Tue 2021-12-21 05:40:23
                Time zone: Etc/GMT-5 (+05, +0500)
System clock synchronized: yes
              NTP service: active
          RTC in local TZ: no
```

Is the Etc/GMT label wrong with the + and -?

Also, if NTP is active, does it take care of DST; i.e. updating time according to UTC setting automatically?. 

Please advise. Thanks.

---

### Post by TheFu on 2021-12-21
If you want DST and ST to be handled correctly, you must use political locations, not relative to UTC.  Whether DST is uses or not is controlled by politics.
There is a command to work through a menu ... Asia/Americas/Europe .... then countries, then cities to pick the one that has the timezone. 

Or you can simply create a /etc/timezone file and put 1 line in there with the political name.  For example, mine is  ....
```
$ more /etc/timezone
America/New_York
```

This shows up as 
```
$ date
Tue 21 Dec 2021 12:22:16 PM **EST**
```
right now.

You can also set an environment variable, TZ, in your ~/.profile.
```
export TZ=America/New_York
```
to control nearly all parts of the system time displays.

This doesn't really impact the locale setting, which controls stuff like whether commas or periods are used and the order that days, months, years are displayed.  For that, check out **localectl**.

If you want a GUI tool for all this, I don't know.  Perhaps the *Ubuntu Desktop Guide* has it?

---

### Post by tc2020 on 2021-12-21
Thanks for your reply.
It makes sense DST applies only when political location is used. Countries in the same UTC time zone may not use DST.
My questions come from how to design user interface to handle time settings in an embedded device. Using only UTC to handle DST as well makes it easier to implement, such as having only one input text box on a web page. Now, it looks like I have to display a list of time zones from timedatectl for users to select.

Relevant to timedatectl and timings in general, I would like to know what goes on with time synchronization among NTP server, system time, and RTC under the following conditions:

- System power on
- System reboot (e.g. sudo reboot)
- NTP server accessible and not accessible
- RTC not accessible

Also, by default, Ubuntu server 20.04 uses ntp.ubuntu.com as its ntp server. Does it have redundancy?. How can I add other NTP servers to the list?. Can I use this default ubuntu ntp setting in production devices that are intended for international use?.

Thanks.

---

### Post by TheFu on 2021-12-21
NTP is the old way. It has some security problems that have been addressed in more modern versions.  NTP is freakin' amazing for how it works and keeps systems with the correct UTC to msec accuracy for pretty much any hardware.

There are thousands of NTP servers around the world. They work in "pools".  These can be set to any NTP server you like or you can run your own, if you prefer. For many situations, having all the systems time synchronized matters, not that they actually have the correct time.  I run an Chrony server on my LAN that all other systems use to sync against.  I've been running a local NTP server since around 1996.  I didn't intend to do this, but Win95 couldn't keep time, while all my Unix systems had no problem at all.  Some machines booted Windows and couldn't keep time - they'd lose 15 minutes in a day, but with Linux or BSD on the exact same hardware, not connected to the internet, they'd be sub-second accurate.  I saw the same time issue with every version of Windows until I stopped using Windows daily around 2008.  It is frustrating to see time on a computer off 5 minutes, report the issue as a huge (Fortune 10 company) to Microsoft and be told that +/- 5 minutes was considered accurate enough by Microsoft for time keeping on their systems.  Pointing out that sub-second accuracy was a solved problem on Unix-based OSes didn't go over well.

For how people synchronize time, that's an individual thing and dependent on their hardware.  If there isn't a built-in clock for the hardware powered by a CMOS battery, then setting time over the network at boot makes sense. I haven't done that in over 20 yrs. Think **rdate** was the command. Regardless, some sort of NTP client was necessary to maintain the time, address drift, and keep the time accurate.

Chronyc has a few commands to track how well it is doing to keep time.
```
$ chronyc sources
210 Number of sources = 1
MS Name/IP address         Stratum Poll Reach LastRx Last sample               
===============================================================================
^* romulus                       3   6   377    14  +3957ns[+8597ns] +/-   35ms

$ chronyc sourcestats
210 Number of sources = 1
Name/IP Address            NP  NR  Span  Frequency  Freq Skew  Offset  Std Dev
==============================================================================
romulus                     8   6   452     +0.001      0.248    +17ns    16us
```

On 20.04 and later, I think Ubuntu installs systemd-timed instead of ntpd.  I disable and mask systemd-timed and use chrony.  systemd-timed didn't keep time to the accuracy I wanted. It wasn't accurate enough to start and stop TV show recordings on my PVR system.  Accurate time is a pet peeve of mine. There's no excuse for any OS today to be off more than 1 second within a month disconnected from the internet. Clocks just aren't the bad anymore.

The political aspects of timezones are fascinating. Some guy in Nebraska or Texas maintains all the timezone files for everyone in the world as a hobby.  About 3x a year, there will be updates, because politicians are constantly screwing around with stuff.  For example, Newfoundland has their own timezone.  US-Eastern or US-Atlantic times weren't close enough for their needs.  Nepal TZ is 15 minutes ahead from India's and 15 min behind Bhutan ... just to be different or is it truly to optimize the time for local needs?

---

