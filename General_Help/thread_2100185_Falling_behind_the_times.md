---
title: "Falling behind the times"
date: 2012-12-31
forum: General Help
---

### Post by niranjan_rao on 2012-12-31
If it was just one machine, I would have blamed it on hardware, but there are multiple ubuntu machines - combo of desktop and servers which are falling behind. They are loosing around 2 minutes every day.

For the desktop machines (12.10), automatically update time from internet is checked and still loosing time. Not sure how to check the settings for server editions. 

Some servers are virtual machines hosted on windows box. Windows box has right time, but servers don't.

I would like to know if automatic time update is really working. If so, which server its referring to get its time entries. How do I find out which server is sending the wrong time information.

---

### Post by 2F4U on 2013-01-01
Time synchronisation is done by NTP. I use it on all my boxes and it is working, but I am usually setting it up "by hand". I don't know your configuration, but instead of using particular servers to synchronise with I am using so called NTP server pools.

[https://help.ubuntu.com/12.04/serverguide/NTP.html](https://help.ubuntu.com/12.04/serverguide/NTP.html)
[http://ubuntuforums.org/showthread.php?t=862620](http://ubuntuforums.org/showthread.php?t=862620)
[http://rbgeek.wordpress.com/2012/04/30/time-synchronization-on-ubuntu-12-04lts-using-ntp/](http://rbgeek.wordpress.com/2012/04/30/time-synchronization-on-ubuntu-12-04lts-using-ntp/)

For a list of available pools see here:

[http://www.pool.ntp.org/en/](http://www.pool.ntp.org/en/)

---

### Post by CaptainMark on 2013-01-01
theyre not dual booting with windows are they? ive heard of weird problems with windows giving a conflicting system time and messing up clocks, i cant imagine why a server would be dual boot though so probably this doesnt apply to you

---

### Post by niranjan_rao on 2013-01-02
I think we managed to trace it down. The machines where time is right are not joined with active directory. We have tinkered some settings on domain contoller and see if helps to keep up with curren time.

---

