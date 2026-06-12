---
title: "Time is jumping back"
date: 2007-02-26
forum: General Help
---

### Post by Ghuul on 2007-02-26
I have some weird problem with time on ubuntu server 6.06.1. Basically system time is jumping few seconds back - ie. if I run "date" command several times I get something like this:

Mon Feb 26 01:43:12 CET 2007
Mon Feb 26 01:43:13 CET 2007
Mon Feb 26 01:43:14 CET 2007
Mon Feb 26 01:43:15 CET 2007
Mon Feb 26 01:43:12 CET 2007 <---- :confused: 
Mon Feb 26 01:43:13 CET 2007
Mon Feb 26 01:43:14 CET 2007
Mon Feb 26 01:43:15 CET 2007
Mon Feb 26 01:43:13 CET 2007 <---- :confused: 

I can't see anything conclusive in logs and if I reboot machine time is correct (it means that machine's RTC works fine). I've tried to kill all unnecessary services but problem persists. Has somebody experienced such problem ? Some recommendations how to trace this problem ?

Machine runs 2.6.15-26-server kernel (i686). Configuration [http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-42769]("http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-42769")

Thanks for any advice


EDIT:
I thought that it could be NTP related but after disabling all time synchronization problem persists...

---

### Post by Ghuul on 2007-03-16
I have replaced motherboard and everything works fine. 
Funny is that Windows Server works without problem on "troublesome" machine :)

---

