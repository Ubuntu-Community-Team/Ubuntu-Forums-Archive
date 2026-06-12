---
title: "Scheduling"
date: 2004-11-01
forum: General Help
---

### Post by jcscar on 2004-11-01
Is there a schedule on Ubuntu that can say, act like an Alarm clock by open up xmms and playing music at 7:45am ??  Granted the computer is on of course.

---

### Post by Cygnia on 2004-11-01
I do something similar but not with xmms. I use a cron job that invokes the play command every morning except for my two days off. To make it easy use kcron or gcrontab if you're a newbie to linux and/or crontab editing. Put the song you want to wake up to in a directory and use the command play /path/to/songfile.

---

### Post by Cygnia on 2004-11-01
Ahem...I just stupidly realized that xmms has an alarm plugin that you could also use. <blush> Guess I was trying to look smart... :oops:

---

