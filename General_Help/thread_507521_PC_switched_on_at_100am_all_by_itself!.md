---
title: "PC switched on at 1:00am all by itself!"
date: 2007-07-23
forum: General Help
---

### Post by oscarsfriend on 2007-07-23
:shock:

I usually switch my PC (running Feisty) off at the point at night, but I forgot last night, and discovered this morning that it had switched itself on.  According to /var/log/syslog.0 this happened at 01:00:38.  I have no idea why this happened.  It can start up by a signal from a PCI/PCIe card (I don't have any), the motherboard LAN (my router was switched off), a timer set from the BIOS (I didn't do that), or a process can use /proc/acpi/alarm to tell it to switch on.  

Now last week I followed [this guide](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake#head-4e445b6254e6a7903e9083b3817d436d054cc83a) to setting up the PC to power itself on.  I'm thinking of turning it into a media centre, and was making sure it could power on by itself.  (I also installed the MythTV front- and backends.)  My initial test was successful, but I have no idea what told it to switch on last night.  Does anyone know what I should be looking for in the /var/log/ files, or have an idea what might have happened?  Any help would be appreciated.

---

### Post by apjone on 2007-07-23
did you do 
```
$ sudo sh -c 'echo "2007-12-12 12:12:12" > /proc/acpi/alarm'
```
or anything similar when following the guide?

---

### Post by oscarsfriend on 2007-07-23
To test it out I did I did this:

> sudo sh -c 'echo "+2000-00-00 00:02:00" > /proc/acpi/alarm'

I shut down and it started up fine about 2mins after I set it.  But that was days ago.

---

### Post by apjone on 2007-07-23
try 
```

cat /proc/acpi/alarm

```
see what that out puts

---

### Post by oscarsfriend on 2007-07-23
Currently it reads:

> 2007-00-00 00:00:00

EDIT: I also just tried setting by clock via the BOIS to just before midnight (=1am with daylight savings), and powering down.  It did not come on again.  So I don't know what's happening!

---

### Post by oscarsfriend on 2007-07-23
Googling about it appears a few people have had a similar problem.  It looks like where the script /etc/init.d/hwclock.sh has been modified to save the alarm after the clock has been set with this line:

```
echo "$ACPITIME" > /proc/acpi/alarm && sleep 1 && echo "$ACPITIME" > /proc/acpi/alarm
```

maybe triggering it to come on at midnight when the value is set to "2007-00-00 00:00:00" (i.e. off).  I'm going to try something like this instead:

```
if [ "$ACPITIME" != "2007-00-00 00:00:00" ]; then
   echo "$ACPITIME" > /proc/acpi/alarm && sleep 1 && echo "$ACPITIME" > /proc/acpi/alarm
fi

```

---

### Post by oscarsfriend on 2007-07-23
The above modification seems to do the trick!  Starts up when I want it to, and doesn't when it gets to 00:00.

---

### Post by oscarsfriend on 2007-07-23
I spoke too soon.  Once an alarm time has passed it resets the date back to 2007-00-00 but the time stays whatever it was (eg. 2007-00-00 16:41:12" -- which will power on my PC at 16:41:12 every day!).  Can anyone tell me how I extract the first part of that "2007-00-00" to check in my above if-statement?  (Or can they tell me before I figure it out myself?)

---

### Post by oscarsfriend on 2007-07-23
OK, I've got it now.  The following should work in all cases:

```
if [ "`echo "$ACPITIME" | sed "s/20..-\(00-00\)\(.*\)/\1/"`" != "00-00" ]; then
   echo "$ACPITIME" > /proc/acpi/alarm && sleep 1 && echo "$ACPITIME" > /proc/acpi/alarm
fi
```

This extracts the month and day of month from the timer info (in the form MM-DD) and checks if it is 00-00, and if it isn't sets the timer.

---

