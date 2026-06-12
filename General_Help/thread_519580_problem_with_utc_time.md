---
title: "problem with utc time"
date: 2007-08-07
forum: General Help
---

### Post by jxb on 2007-08-07
i'm running ubuntu 6.06 server in a vmware on windows server 2003. my windows server and the bios of the vmware always show the correct time, but my ubuntu installation shows the wrong utc time! the utc time of my ubuntu is always 2 hours ahead of the real utc time. 

i have already created a cron.daily ntpdate job snychronising my server's time, but it's still wrong. any ideas?

---

### Post by ajgreeny on 2007-08-07
Just out of interest did you ask to set to utc when you installed ubuntu, and do you dual boot with windows?  Sorry, but now I see you run vmware, which I didn't notice at the start.

Anyway, just in case it helps, I'll continue.
I know from previous installations that it is much better and accurate to set your time to local not utc when installing if you do have windows as well, otherwise everytime you boot into windows there is a reset of the time to local windows time, and then when you are back in ubuntu the time will be an incorrect utc, in Vienna this will be two hours ahead of standard utc, I think.

If you want to try this out you can change it by setting  UTC=no in /etc/defaults/rcS        This will set the time to local instead of GMT (UTC).

---

### Post by jnorthr on 2007-08-07
sounds like the UTC co-ordinate in ubuntu is set to a time zone ahead of your server timezone. Try right click on date/time in menu bar to see if you can open dialog to see what timezone ubuntu thinks it is. You may be able to reset it from there.

---

### Post by jxb on 2007-08-07
while installing i ticked 'use utc time' but i changed that in the /etc/default/rcS file to no and the time is still wrong.

i don't have gnome installed but in the tzconfig file my timezone is set to vienna/austria. when i reconfigure the tzconfig file it shows me at the end:

Your default time zone is set to 'Europe/Vienna'.
Local time is now:      Die Aug  7 17:07:46 CEST 2007.
Universal Time is now:  Die Aug  7 15:07:46 UTC 2007.
 
also the correct time would be 15:07 vor local time and 13:07 for utc time.

---

