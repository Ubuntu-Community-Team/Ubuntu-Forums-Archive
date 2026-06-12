---
title: "Crontab error with clamav installed"
date: 2005-06-03
forum: General Help
---

### Post by word_virus on 2005-06-03
Hey, folks!  Just a quick (hand-holding) question here, if someone's got a sec.

Cron.daily's been leaving me mail all week that looks like this:

/etc/cron.daily/logrotate:
/tmp/logrotate.r9SSno: line 4: /etc/init.d/clamav-daemon: No such file
or directory
error: error running postrotate script
run-parts: /etc/cron.daily/logrotate exited with return code 1

The error, here, obviously is that there's no /etc/init.d/clamav-daemon, which is true.  There is, however, a (not at my computer right now, so guesstimating) freshclam-updater.  Am I safe just changing this line in the crontab?  This this worth filing a bug report about?

Thanks!!

---

