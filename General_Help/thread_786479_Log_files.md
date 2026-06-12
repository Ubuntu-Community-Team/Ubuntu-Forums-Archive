---
title: "Log files"
date: 2008-05-08
forum: General Help
---

### Post by ginge6000 on 2008-05-08
I installed Hardy last week as a dual boot on my computer.  Ever since then it will, after about 5 - 20 minutes of use, freeze.  The mouse and keyboard become unresponsive and I have to do a hard reset.  At first it seemed to do it whilst using Firefox so I downgraded to v2 and it happened a little less frequently.  What I am wondering is whether there may be a particular log file to look at to see what was occurring at the time of the crash so I can see if there is a pattern.  Can anyone suggest which log file (and its location) I should have a look at?

---

### Post by Monicker on 2008-05-08
System -> Administration -> System Log

Start with /var/log/messages, then try daemon.log and syslog.

---

