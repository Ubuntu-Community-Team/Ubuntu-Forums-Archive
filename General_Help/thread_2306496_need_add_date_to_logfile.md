---
title: "need add date to logfile"
date: 2015-12-16
forum: General Help
---

### Post by wuname on 2015-12-16
I'm new to Ubuntu OS, and I want to add date to logfile , here is current way:
program >> log [return man 3 unblocked]("http://qingzhiliao.com/return-man-3-the-season.html")
tail -f log | while read line; do echo `date` "$line" ; done >> log-date
tail -f log-date


How can [I]("http://www.shjlsyys.com/23-nationstar-mortgage-class-action.html") make that easier?
THank you!

---

### Post by ian-weisser on 2015-12-16
That seems pretty easy already.
Can you change 'program' to add the datestamp during it's run?
If 'program' logs to a logfile goverened by (daily) logrotate, it doesn't need a datestamp. The file creation date is the clue.

---

