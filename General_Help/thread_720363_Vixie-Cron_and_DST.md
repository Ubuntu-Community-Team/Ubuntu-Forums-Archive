---
title: "Vixie-Cron and DST"
date: 2008-03-10
forum: General Help
---

### Post by CrucialCa on 2008-03-10
I'm using vixie-cron on a number of systems and I'm not quite clear on how vixie-cron handles jobs during the 2am-259am hour on DST changeover-days.  

Are the jobs performed at their "regular" time (aka a 2:30 job will run 1 hour after 1:30?), or are they simply skipped and its up to the admin to manage how they will run.  

Just looking for some clarification here.  I checked google, but could not come up with the answer.  

Thanks in advance

---

### Post by Oldsoldier2003 on 2008-03-10
> **CrucialCa said:**
> I'm using vixie-cron on a number of systems and I'm not quite clear on how vixie-cron handles jobs during the 2am-259am hour on DST changeover-days.  

Are the jobs performed at their "regular" time (aka a 2:30 job will run 1 hour after 1:30?), or are they simply skipped and its up to the admin to manage how they will run.  

Just looking for some clarification here.  I checked google, but could not come up with the answer.  

Thanks in advance

not sure about vixie cron but cron handles dst as a minor time adjustment.
[QUOTE=man cron]      
       Special  considerations  exist when the clock is changed by less than 3
       hours, for example at the beginning and end of daylight  savings  time.
       If  the time has moved forwards, those jobs which would have run in the
       time that was skipped will be run soon after the  change.   Conversely,
       if  the  time has moved backwards by less than 3 hours, those jobs that
       fall into the repeated time will not be re-run.

       Only jobs that run at a particular time (not specified as @hourly,  nor
       with  ’*’ in the hour or minute specifier) are affected. Jobs which are
       specified with wildcards are run based on the new time immediately.

       Clock changes of more than 3 hours are considered to be corrections  to
       the clock, and the new time is used immediately.
[/QUOTE]

---

### Post by CrucialCa on 2008-03-10
Thanks for the reply and information.  That explanation makes sense, but none of my 2am-259am jobs ran on Sunday morning.  I'm still trying to determine what happened.  

Thanks again for any help

---

