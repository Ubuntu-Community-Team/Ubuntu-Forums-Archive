---
title: "Ubuntu Clock Possessed by Demons / Interesting &amp; Annoying"
date: 2008-03-10
forum: General Help
---

### Post by YWELLC on 2008-03-10
I am having an annoying / interesting situation with my Ubuntu clock.

Dual booting 64bit Gutsy and XP Pro.  When I boot Ubuntu my clock is 4 hours behind (this happens by the time I get to the login screen) , despite the Time Zone setting still being correct..  Initially I thought I needed to replace my CMOS battery.  This theory was based on clock issues in both operating systems.  Upon further review I found that the system clock BIOS settings were only off after a boot / shutdown of Ubuntu.  When I boot and manually set the BIOS clock settings, XP reflects the proper (just set)  time upon load.  If I hard reset and reboot XP again the BIOS and XP clock settings stay the same (and are correct and identical).  If I boot into Ubuntu the clock goes back 4 hours.

I have searched around for similar posts and have found no solution.  I do not think it is a UTC issue (/etc/default/rcS UTC=no):

htp://ubuntuguide.org/wiki/Dapper#How_to_disable_system_time.2Fdate_from_being_reset_to_UTC_.28GMT.29

Anyway last piece of info, I am fairly sure about the 4 hour detraction being accurate as I did the following:

Hard reset, manually edit BIOS time to reflect real time,  booted Ubuntu into recovery mode to watch for boot errors (got several: "Superblock last write time is in the future. FIXED").  Typed "exit" to reboot from the prompt, auto-reboot into normal mode, TA DA, system clock is 8 hours behind recently set BIOS time.

Any help would be greatly appreciated.

---

### Post by Spenzer4Hire on 2008-03-10
I'm no expert for sure, but you should look into the UTC issue again.  If your profile is right and you're in Washington D.C. and it is Daylight Savings Time, you are 4 hours behind GMT (assuming I did my math right).  This accounts perfectly for your anomaly.  If UTC is off, is your Ubuntu time zone set properly?  Sorry I can't be of more help, but it has to be related.

---

### Post by YWELLC on 2008-03-10
I thought so as well after I checked the other posts, but

Tray Clock - Preferences:

Clock Type: 12 hour
show seconds - unchecked
show date - unchecked
Use UTC - unchecked

/etc/default/rcS:
TMPTTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=no
VERBOSE=no
FSCKFIX=no

Be happy to look into this again if there is any other place to check.  Thanks for your reply.

---

### Post by smartboyathome on 2008-03-10
What happens when you set UTC to yes?

---

### Post by Spenzer4Hire on 2008-03-10
To check which time zone Ubuntu is set to type date at the command line.  For you I think it should say EDT just before the year.  Is this correct?

---

### Post by YWELLC on 2008-03-10
Time Zone set properly to EDT, via :~$time, and in the tray, time/date, adjust date/time "America/New_York"

Boot with UTC=yes in /etc/default/rcS yields same result -> 4 hours behind the correct time.

---

### Post by astrotech226 on 2008-03-10
I think Spenzer4Hire is on the right track.  Check a few things from the command line.  What's the output of:

```
hwclock
date
```

When you shut down Ubuntu, it looks like it's syncing the hardware clock to the system clock.  This explains why the time goes off by four hours after booting into Ubuntu and restarting.

You can also try this from the command line:
```

sudo dpkg-reconfigure tzdata
```

I think all this really does is rebuild the /etc/localtime file based on your input.  On other systems, this is a symlink to the timezone is /usr/share/zoneinfo

---

### Post by YWELLC on 2008-03-10
hwclock and date show same time.  Oddly UTC time is correct time:

:~:hwclock
Mon 10 Mar 2008 7:22:50 PM EDT -1.034523 seconds

:~date
Mon Mar 10 19:22:56 EDT 2008

sudo dpkg-reconfigure tzdata
Current default timezone: 'America/New York'
Local time is now: Mon Mar 10 19:23:25 EDT 2008
Universal time is now: Mon Mar 10 23:23:35 UTC 2008

---

### Post by YWELLC on 2008-03-10
/etc/init.d/ has two scripts on my computer (that are immediately identifiable by me) as being related to the system and hardware clocks / UTC settings / loading & saving.

I looked through the code, though I am no expert; please find attached:


_hwclock.sh_
[ATTACH]62247[/ATTACH]
[U]
hwclockfirst.sh[/U]
[ATTACH]62248[/ATTACH]

---

### Post by astrotech226 on 2008-03-11
> **YWELLC said:**
> 
sudo dpkg-reconfigure tzdata
Current default timezone: 'America/New York'
Local time is now: Mon Mar 10 19:23:25 EDT 2008
Universal time is now: Mon Mar 10 23:23:35 UTC 2008

This is definitely not right.  Your UTC time should 4 hours ahead putting you into Mar 11th.

---

### Post by astrotech226 on 2008-03-11
I think the option in /etc/default/rcS for UTC should be set to YES.

```
TMPTTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=yes
VERBOSE=no
FSCKFIX=no
```

You should probably reboot after that to ensure a clean test.  Log in and set the time.  I would do this from the command line for this test.

```
sudo date MMDDhhmm
```

Then set the hardware clock to your system clock:

```
sudo hwclock --systohc
```

Reboot once more and see what happens.

---

### Post by YWELLC on 2008-03-11
I have set the /etc/default/rcS -> UTC=yes, rebooted, manually set :~$date on the command line then, rebooted to no avail.

I will try the whole process over with your suggestion of setting the (now accurate) hwclock to the systohc, then reset, when I get home to my linux box and report the findings.

---

### Post by astrotech226 on 2008-03-11
Here's another thread where they have the same problem that you do.  It looks similar to the steps you have already tried, but with a few minor changes.  Give this a try also and see how it works.

```
http://ubuntuforums.org/showthread.php?t=683986
```

---

### Post by YWELLC on 2008-03-12
After going through the other post(s) I followed your last set of instructions to the letter.  Synchronizing with 

~:$hwclock --systohc

seemed to do the trick.  Multiple successful boots with the proper UTC time displayed (checked the BIOS clock in between as well).  I changed back to UTC=no in the rcS file and lo and behold my system reflects the proper time.

While I still have no idea or understanding of what caused the original fork in functionality I am extremely pleased that it is working properly again.  

Thank you so much for all of your assistance.

---

