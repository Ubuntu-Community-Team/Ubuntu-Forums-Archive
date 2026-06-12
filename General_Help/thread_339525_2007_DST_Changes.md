---
title: "2007 DST Changes"
date: 2007-01-15
forum: General Help
---

### Post by skrieg on 2007-01-15
What needs to be done to server 6.06.1 for the 2007 daylight savings time changes?  Is there a patch or an update file available?

---

### Post by fcsnc on 2007-01-25
::bump::  me too, please.  Is this covered somewhere in the forums?

DST in most of the United States begins March 11 this year.  Not that many weeks away!
:confused:

---

### Post by Blackneto on 2007-01-26
try this:
> xxx@xxx:~$ sudo zdump -v /etc/localtime |grep 2007
/etc/localtime  Sun Mar 11 07:59:59 2007 UTC = Sun Mar 11 01:59:59 2007 CST isdst=0 gmtoff=-21600
/etc/localtime  Sun Mar 11 08:00:00 2007 UTC = Sun Mar 11 03:00:00 2007 CDT isdst=1 gmtoff=-18000
/etc/localtime  Sun Nov  4 06:59:59 2007 UTC = Sun Nov  4 01:59:59 2007 CDT isdst=1 gmtoff=-18000
/etc/localtime  Sun Nov  4 07:00:00 2007 UTC = Sun Nov  4 01:00:00 2007 CST isdst=0 gmtoff=-21600


if you have results similar to above you should be okay. if not you may have a non-standard setup and will have to update your tzdata manually. or update to the latest libc6 package.

most recent distro's are okay.

---

### Post by jkeyes0 on 2007-02-23
> **Blackneto said:**
> try this:


if you have results similar to above you should be okay. if not you may have a non-standard setup and will have to update your tzdata manually. or update to the latest libc6 package.

most recent distro's are okay.

Thx very much for this. Co-workers who run Ubuntu were getting antsy about it. I was unconcerned.

---

### Post by tlyczko on 2007-03-07
> **Blackneto said:**
> try this:


if you have results similar to above you should be okay. if not you may have a non-standard setup and will have to update your tzdata manually. or update to the latest libc6 package.

most recent distro's are okay.

I get the following results:

> sudo zdump -v /etc/localtime |grep 2007
/etc/localtime  Sun Mar 11 06:59:59 2007 UTC = Sun Mar 11 01:59:59 2007 EST isdst=0 gmtoff=-18000
/etc/localtime  Sun Mar 11 07:00:00 2007 UTC = Sun Mar 11 03:00:00 2007 EDT isdst=1 gmtoff=-14400
/etc/localtime  Sun Nov  4 05:59:59 2007 UTC = Sun Nov  4 01:59:59 2007 EDT isdst=1 gmtoff=-14400
/etc/localtime  Sun Nov  4 06:00:00 2007 UTC = Sun Nov  4 01:00:00 2007 EST isdst=0 gmtoff=-18000

What should I do??

I'm on 6.06, it is only running vmware server 1.01 and webmin and apcupsd.

Thank you, Tom

---

### Post by tlyczko on 2007-03-07
Which update package do I have to install to get things right again??

Just run the basic update request, whatever it is, through Webmin??

Thank you, Tom

---

### Post by wglenncamp on 2007-03-07
> **tlyczko said:**
> I get the following results:

> sudo zdump -v /etc/localtime |grep 2007
/etc/localtime  Sun Mar 11 06:59:59 2007 UTC = Sun Mar 11 01:59:59 2007 EST isdst=0 gmtoff=-18000
/etc/localtime  Sun Mar 11 07:00:00 2007 UTC = Sun Mar 11 03:00:00 2007 EDT isdst=1 gmtoff=-14400
/etc/localtime  Sun Nov  4 05:59:59 2007 UTC = Sun Nov  4 01:59:59 2007 EDT isdst=1 gmtoff=-14400
/etc/localtime  Sun Nov  4 06:00:00 2007 UTC = Sun Nov  4 01:00:00 2007 EST isdst=0 gmtoff=-18000

What should I do??

I'm on 6.06, it is only running vmware server 1.01 and webmin and apcupsd.

Thank you, Tom

Nothing.  Everything looks good.  March 11th begins DST (New) and Nov 4th ends DST (New).  You're good to go!

---

### Post by jfdill_2 on 2007-03-08
> **tlyczko said:**
> What should I do??

I'm on 6.06, it is only running vmware server 1.01 and webmin and apcupsd.

Thank you, Tom

Find someone with a W2K or earlier computer and rub it in their face. :biggrin:

---

### Post by JimTDI on 2007-03-10
> **Blackneto said:**
> try this:


if you have results similar to above you should be okay. if not you may have a non-standard setup and will have to update your tzdata manually. or update to the latest libc6 package.

most recent distro's are okay.

Thanks much for this info!!

---

### Post by floundered on 2007-03-11
My Ubuntu 6.10 system was fully updated March 10, yet this morning when I booted up at 8:30PDT the time was shown as 7:30.  In addition, a GNOME control panel had tried to open after I logged in, but the window was about 10 pixels wide by 20 pixels high, such that only the window frame corners could be seen (sorry, I forget the actual name of the application).  When I tried to resize it to see what it was, it didn't comply.  So I right-clicked on the task bar button to maximize the window, after which the thing crashed and generated a bug report.  In keeping with the kind of morning it's been, the bug reporting tool claimed that it didn't know the name of the application for which it was generating a report...

Frustrated, I left the clock at 7:30 and rebooted into (gasp) XP, which corrected the clock just fine.

After a while I rebooted back into Ubuntu again (am there now) and the clock seems correct.  So I have a few questions:  

[LIST=1]
[*]Through the GNOME clock UI, how can I see whether DST is active or not?
[*]What was the expected behaviour at bootup for the DST change?  Should I have received a GUI dialog or something?
[*]Why was that window ultra-small?  I've had this with the configuration dialog for the TabMixPlus plugin  for FireFox before, but never for anything else.  I also have Beryl installed, in case that may be related.
[/LIST]

Thanks!  I hope the DST change went smooth for everyone else.

---

### Post by bobbob1016 on 2007-03-17
It MIGHT be that Ubuntu was using your BIOS' time, and the BIOS' time was wrong.  XP MIGHT have fixed the BIOS' time, but I'm not sure.  Just a guess.

---

### Post by shingalated on 2007-03-17
If you setup your computer to sync with an NTP server, it will change automagically, and you should be fine. :)

---

### Post by jfdill_2 on 2007-03-17
> **shingalated said:**
> If you setup your computer to sync with an NTP server, it will change automagically, and you should be fine. :)

NTP syncs UTC time, not the local timezone.  UTC time will be fine, but if the offset from UTC for your local timezone is wrong, the clock will be wrong regardless of NTP.

---

