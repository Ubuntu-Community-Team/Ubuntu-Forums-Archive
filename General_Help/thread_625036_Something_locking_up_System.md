---
title: "Something locking up System"
date: 2007-11-27
forum: General Help
---

### Post by richcoosa19 on 2007-11-27
For some time now, I have noticed that my system will not run top.  When I run uptime, it always says the same load averages:
15:35:04 up  4:49,  3 users,  load average: 0.99, 0.97, 0.91

The system still handles http requests through apache, and it still runs queries in mysql.  However, I would like to know what's going on since I can't run top or get a clear load average.



VMWARE Virtual Computer running on XP Pro
Intel PentiumD 3.0GHz
1.0 GB RAM
 Using XFS on LVM
Ubuntu 7.10 Server - Gutsy Gibbon
Mysql 5.0.45
Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6 mod_perl/2.0.2 Perl/v5.8.8 Server

---

### Post by richcoosa19 on 2007-11-28
There seems to be something runnning around 5:00AM that's resetting the time on the server to some time in the year 1930....lol

I have cleared all of my cron jobs and am going to do a reboot this evening, I'll repost telling the outcome.

---

