---
title: "Daylight Saving Time Issues"
date: 2007-10-28
forum: General Help
---

### Post by winterhighland on 2007-10-28
The UK switched from Summer Time to GMT at 2am this morning (clocks back an hour) and remote xubuntu boxes controlling some webcams that I run initially correctly handed the change. The timestamps on the webcam images were the correct GMT time, so xubuntu handled the end of DST.

However at 11.08am this morning the machines reverted to back to DST... :confused:

Any ideas? Unfortunately we have no way of remotely accessing these particular  boxes, so from here I cant gather any further info than I have above. There is a cronjob that kicks in at 11am daily to delete a log created by the camera operating script, but the camera operating scripts are called by a cron job that runs every 3 minutes anyway.

---

### Post by PetriSirk on 2007-10-29
Hi, 

For me the Gutsy Gibbon changed to wrong direction in time. Instead of subtracting one hour in the end of DST it added one. How hard can it be? Could someone make a test case?

Details:
Linux xxxx 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU
#
# /etc/default/rcS

TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=yes
VERBOSE=no
FSCKFIX=no

Using time servers:
tick.keso.fi
fartein.ifi.uio.no
-Pete

---

### Post by speckman on 2007-10-29
In America, we have a stupid new law that pushes back daylight saving time to November 4th this year.  So, my time in Gutsy was changed too early (but it was changed in the right direction).  I almost missed work!  I wonder if the stupid lawmakers thought of all of the software that's going to be buggy this year.

---

### Post by speedwell68 on 2007-10-29
> **PetriSirk said:**
> Hi, 

For me the Gutsy Gibbon changed to wrong direction in time. Instead of subtracting one hour in the end of DST it added one. How hard can it be? Could someone make a test case?

Details:
Linux xxxx 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU
#
# /etc/default/rcS

TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=yes
VERBOSE=no
FSCKFIX=no

Using time servers:
tick.keso.fi
fartein.ifi.uio.no
-Pete

If you are using time servers surely the problems lie there.  If it is synchronised with a time server then it will only display the time it is told to.  I am using ntp2a.mcc.ac.uk .

---

### Post by Perpetual on 2007-10-29
Yes, you can hardly blame the OS for errors on the time server.  I'm in the states using ntp-0.cso.uiuc.edu (Illinois) and my time did not change.

Also, this isn't the first time time changes have been delayed/corrected throughout history.

---

### Post by matey3 on 2008-03-31
> **speckman said:**
> In America, we have a stupid new law that pushes back daylight saving time to November 4th this year.  So, my time in Gutsy was changed too early (but it was changed in the right direction).  I almost missed work!  I wonder if the stupid lawmakers thought of all of the software that's going to be buggy this year.

sorry to be off subject but I am fed up too. watch google videos by Jordan Maxwell and see who these politicians really are.. we need to be free ppl again,. to hell with "liberty"!

BTW I am struggling with this stupid time change as well. our telephones times  (VoIP) are wrong!? the servers did not change to new time neither!? and i lost a bunch sleep! 

BTW they just realized that ppl have a lot more car crashes/accidents  than usual after the time change! another "bright" decision from those (not so) bright politicians!
Be Safe, drive carefully!

---

