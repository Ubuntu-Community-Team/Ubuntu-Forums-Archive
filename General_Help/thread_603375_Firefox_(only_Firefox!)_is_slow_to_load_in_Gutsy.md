---
title: "Firefox (only Firefox!) is slow to load in Gutsy"
date: 2007-11-05
forum: General Help
---

### Post by philips999 on 2007-11-05
I´ve found several ¨firefox is slow¨ threads, but none that describe my problem.

I´m running 64-bit Ubuntu Gutsy.  Until the recent upgrade from Feisty, everything was fine.

Since then, pages in Firefox (and Firefox derivatives such as Swiftweasel) load slowly.  This seems to be a particular problem where the page pulls in images or adverts from another server.  The page load gets stuck at the ¨Tranferring data from...¨ stage.  After about a minute or two, the page eventually loads OK.

This problem does NOT affect Konqueror or Opera (although Opera´s running on a 32-bit chroot, so that may not be a fair comparison).  All other web things, such as bittorrent or gnutella seem fine.

I´ve checked DNS, and that is as stated by my ISP.  I´ve tried turning ipv6 on and off both in about:config and in /etc/hosts as desribed widely on the web.  I´ve checked ¨dig¨ and traceroot but there´s nothing unusual there that I can see.

Apart from saying ¨well, just use Konqueror¨ - which is what I'm doing! - any ideas?

---

### Post by NexusGS on 2007-11-05
Well,i get the same problem in a way...Sometimes,Firefox stucks at the ¨Tranferring data from...¨ stage,but my problem is that at the same time,Opera,weatherforecast or anything else i try to do that time and hasn't already established a connection (for example shoutcast doesn't stop or bittorent traffic is not affected) cannot connect...All that for about 1-2 minutes.Then afterwards,all work again and after an a period of time (not standar,can be from a few seconds till a few minutes) i get the same problem again..To be honest i haven't checked if i get the same problem at Windows but i think i have it...If i have the same problem in Windows,i guess it's my ISP problem or my router's.

Anyone with the same problem that has tested it?

---

### Post by s.victor on 2007-11-06
Have you assigned DNS servers?

Add these ([www.opendns.com]("http://www.opendns.com/")) as your DNS addresses:
208.67.222.222
208.67.220.220

It may speed up your Firefox. It worked for me.

---

