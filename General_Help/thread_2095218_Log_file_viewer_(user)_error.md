---
title: "Log file viewer (user) error"
date: 2012-12-16
forum: General Help
---

### Post by cogset on 2012-12-16
I've manually added a vlc_log file in /var/log/ to try to monitor VLC activity and then opened it with the log file viewer:now that I've deleted that file,the log viewer shows this warning when starts:
> Error stating file '/var/log/vlc_log': No such file or directory
how can I get rid of it? I've had a look at the rsyslog.conf file in /etc hoping to find some reference to this vlc_log file but there isn't any.

---

### Post by Cheesemill on 2012-12-16
Fire up gconf-editor (you may need to install it first) and edit the /apps/gnome-system-log/logfiles entry.

---

### Post by cogset on 2012-12-17
Thanks a lot ;) ,that is exactly what I was after:there's so much (to me,incomprehensible) stuff in  gconf-editor that I usually steer clear of it and try to find a config  text file that I can comfortably edit instead.

---

