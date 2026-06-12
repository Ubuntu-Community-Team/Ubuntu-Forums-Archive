---
title: "UTC problem"
date: 2015-06-17
forum: General Help
---

### Post by alessandro21 on 2015-06-17
Hi all, I've a problem, I've to set the time to UTC and I did that, but how can I set it to UTC+1/UTC+2 ecc.?
Thanks, I've to set it to UTC, in GMT I've problem with Windows and Yosemite.

---

### Post by Bashing-om on 2015-06-17
alessandro21; Hello ;

OK; Windows :
> 
GMT I've problem with Windows and Yosemite.

Windows sets the hardware clock to local time by default. Linux/Unix sets it to UTC by default. One of them needs changing so they both use the clock the same way. -> 
[http://askubuntu.com/questions/169376/clock-time-is-off-on-dual-boot](http://askubuntu.com/questions/169376/clock-time-is-off-on-dual-boot)
To tell your Ubuntu system that the hardware clock is set to 'local' time:

edit " /etc/default/rcS "
add or change the following section
 # Set UTC=yes 
if your hardware clock is set to UTC (GMT)
UTC=no
You need to have root privileges, which means using sudo.
 Windows defaults to considering the hardware clock to being local time. Ubuntu (and pretty much all *NIX systems) defaults to considering the hardware clock to be UTC. So every time you boot Windows it's "fixing" the hardware clock, and setting it back X hours from UTC to your local time.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by alessandro21 on 2015-06-17
> **Bashing-om said:**
> alessandro21; Hello ;

OK; Windows :

Windows sets the hardware clock to local time by default. Linux/Unix sets it to UTC by default. One of them needs changing so they both use the clock the same way. -> 
[http://askubuntu.com/questions/169376/clock-time-is-off-on-dual-boot](http://askubuntu.com/questions/169376/clock-time-is-off-on-dual-boot)
To tell your Ubuntu system that the hardware clock is set to 'local' time:

edit " /etc/default/rcS "
add or change the following section
 # Set UTC=yes 
if your hardware clock is set to UTC (GMT)
UTC=no
You need to have root privileges, which means using sudo.
 Windows defaults to considering the hardware clock to being local time. Ubuntu (and pretty much all *NIX systems) defaults to considering the hardware clock to be UTC. So every time you boot Windows it's "fixing" the hardware clock, and setting it back X hours from UTC to your local time.[INDENT][INDENT]my bit to try and help
[/INDENT]
[/INDENT]


I have UTC in all O.S. so I need to set UTC +2 in Ubuntu, because it goes back of two hours. What should I do?

---

### Post by Bashing-om on 2015-06-17
alessandro21; Well ...

The obvious thing is too look at what is presently set for how the ubuntu system handles the setting of the hardware clock:
Post back the output - Between code tags - of terminal command:
```

cat /etc/default/rcS

```
And direct advise will be provided.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

We are smarter that the computer
[INDENT][INDENT]tell the computer what to do
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2015-06-17
I will admit it. I am a little confused. So, I may be looking at this all wrong.

I have my systems set to local time which is London, UK, and at present it is British Summer Time (BST) which is 1 hour ahead of UTC. Because Ubuntu On Air sessions go by UTC I have added UTC as a location using Time & Date settings. So, when I click on the calender indicator icon and can see the time as both London time and UTC.

When BST ends Ubuntu will automagically set London time to Greenwich Mean Time (GMT). It does this because Ubuntu gets regular updates of the Time Zone database (tz data).

Add locations that are +1 hour offset of UTC and +2 hour offset of UTC. Places in Africa are 1 or 2 hours in front of UTC. As are places in Europe. Places in America are behind UTC and places in Asia are several hours in front of UTC. 

[https://en.wikipedia.org/wiki/List_of_tz_database_time_zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)

Regards.

---

### Post by NoWayWin8 on 2015-06-17
```
$ sudo dpkg-reconfigure tzdata
```
When it asks you for location select "none of the above", then it will take you to menu to set time as a GMT offset.

---

### Post by NoWayWin8 on 2015-06-17
To display additional time zones, click on the clock then "time and date settings", "Clock" tab, then click "time in other locations" and the "Choose locations" button to add other geographic locations to display time in.

---

### Post by alessandro21 on 2015-06-18
> **Bashing-om said:**
> alessandro21; Well ...

The obvious thing is too look at what is presently set for how the ubuntu system handles the setting of the hardware clock:
Post back the output - Between code tags - of terminal command:
```

cat /etc/default/rcS

```
And direct advise will be provided.

```
#
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.

# delete files in /tmp during boot older than x days.
# '0' means always, -1 or 'infinite' disables the feature
#TMPTIME=0

# spawn sulogin during boot, continue normal boot if not used in 30 seconds
#SULOGIN=no

# do not allow users to log in until the boot has completed
#DELAYLOGIN=no

# assume that the BIOS clock is set to UTC time (recommended)
UTC=no

# be more verbose during the boot process
#VERBOSE=no

# automatically repair filesystems with inconsistencies during boot
#FSCKFIX=no


```
It says UTC=no, but I have set the location to UTC, I've to set to UTC+2

---

### Post by alessandro21 on 2015-06-18
> **NoWayWin8 said:**
> ```
$ sudo dpkg-reconfigure tzdata
```
When it asks you for location select "none of the above", then it will take you to menu to set time as a GMT offset.
I know, but I have to set UTC with offset.

---

### Post by Bashing-om on 2015-06-18
alessandro21; Hey;

I would expect:
> 
It says UTC=no, but I have set the location to UTC, I've to set to UTC+2

setting " UTC=no ' to have corrected the time disparity . Such is not the case ?
What now is the situation between ubuntu/Windows/ and applications ?

[INDENT][INDENT]sometimes;
[INDENT][INDENT][INDENT]all we can do is try and see 
[INDENT][INDENT][INDENT][INDENT]what happens
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by VMC on 2015-06-18
> **grahammechanical said:**
> I will admit it. I am a little confused. So, I may be looking at this all wrong.

....

UTC and time in general has always caused confusion. It's a problem using Clonezilla, but that's another issue.

My 'rcS' is always set  'UTC=no'

---

### Post by efflandt on 2015-06-19
I always thought that something like this would set the CMOS clock/calendar to system time and let Linux know that CMOS is localtime:```
sudo hwclock -w --localtime
```Of course that relies on your system time being correct initially.

---

