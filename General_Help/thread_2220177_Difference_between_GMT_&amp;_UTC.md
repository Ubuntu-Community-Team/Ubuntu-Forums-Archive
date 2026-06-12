---
title: "Difference between GMT &amp; UTC"
date: 2014-04-27
forum: General Help
---

### Post by Holmes.Sherlock on 2014-04-27
Time was being shown wrong after I installed Ubuntu 14.04. So, here's what I did.

> 
**sudo dpkg-reconfigure tzdata**


Current default time zone: 'Asia/Kolkata'
Local time is now:      Sun Apr 27 16:21:41 IST 2014.
Universal Time is now:  Sun Apr 27 10:51:41 UTC 2014.


**sudo dpkg-reconfigure tzdata**


Current default time zone: 'Etc/GMT'
Local time is now:      Sun Apr 27 10:52:52 GMT 2014.
Universal Time is now:  Sun Apr 27 10:52:52 UTC 2014.


When I selected *None of the above* --> GMT, local time got changed to to GMT from IST. How does IST, GMT, UTC differ?

---

### Post by bapoumba on 2014-04-27
[http://www.worldtimebuddy.com/utc-to-ist-converter](http://www.worldtimebuddy.com/utc-to-ist-converter)
IST : India Standard Time > UTC + 5h30
UTC : Universal Standard Time
GMT : Greenwich Mean Time

Basically, GMT = UTC. UTC is now the universal convention. [https://en.wikipedia.org/wiki/Greenwich_Mean_Time](https://en.wikipedia.org/wiki/Greenwich_Mean_Time)

---

