---
title: "Slow HTTP performance"
date: 2007-02-09
forum: General Help
---

### Post by Kiamo on 2007-02-09
Hello,
I have an app which is using libCURL to fetch web data (just text stuff), process it and store some stuff in a MySQL database.  I have this app and the db running on an Ubuntu machine.
Recently I have the app tracking how much time is spent total across all threads at certain tasks.  In Linux, ~95% of the time with 10 threads is spent waiting to recieve data (waiting on CURL to return, basically).  If I run the same app in Windows (connecting to the same db over a LAN) on the same internet connection, it spends just ~65% waiting on data.  It seems to process HTTP stuff much faster for some reason.

I asked the writer of libCURL and he suggested a misconfiguration on the Linux machine.  Its a pretty base Ubuntu install.  Network adaptor is a NetGear FA311 10/100 PCI card, processor is an Athlon XP 2200+ and the machine has 1 GB of DDR RAM.  Internet connection is a 6/1 mbps fiber line (LAN is 100 mbps).  I have tried building the latest libCURL from source and with c-ares with no noticable improvement.

I have no idea if anyone could know why this would happen, but I just thought I'd ask.  If there was anything I figured the Linux machine would win at, it was networking.  I musta done something wrong.  hah.  On the Windows box I can update ~10 sites per second, but on the Linux machine, it struggles to maintain 4.  :(

Oh, by the way, the box pings fine (~19 ms to Google.com) and seems to operate ok.  CPU use is idle while waiting on CURL, memory use normal, network not maxed, just idle until data (somewhat slowly) comes in.


Thanks for any ideas!

---

### Post by scrooge_74 on 2007-02-09
You just have to make some adjustments to your Linux configuration.

[This link]("http://doc.gwos.org/index.php/DisableIPV6") should help you

---

### Post by resist- on 2007-02-09
Are you using Firefox ? I had the same problem, and i just followed instructions specified there:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_load_Web_site_faster_in_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_load_Web_site_faster_in_Mozilla_Firefox)


I heard IPv6 really slowing down... Did all those things, and browsing felt smoother...

Hope this helps

---

