---
title: "Update notification not working"
date: 2007-11-29
forum: General Help
---

### Post by eroica on 2007-11-29
hello,
Upon installing gutsy I no longer get automatic update notification. I have a notification area in my panel and once i run System>Admin>Update manager and do a manual check I see updates and the notification icon appears in my system tray. Any ideas on what's wrong I have a snapshot of my update notifier settings attached.

---

### Post by geirha on 2007-11-29
Does ```
ps -ef | grep [u]pdate-notifier
``` in a terminal output anything? If not, you should check System->Preferences->Sessions, and add update-notifier as a startup program.

---

### Post by eroica on 2007-11-30
ps -ef | grep [u]pdate-notifier
*****    5167  4978  0 08:22 ?        00:00:00 update-notifier

that was the first thing I had checked was to see if the update notifier was running in the session manager which it is.

---

