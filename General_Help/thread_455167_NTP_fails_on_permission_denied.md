---
title: "NTP fails on permission denied"
date: 2007-05-26
forum: General Help
---

### Post by elspxvwcyr on 2007-05-26
I am running Ubuntu 7.04. I enabled NTP but it was apparent that it was not working (although ntpd is running as a process). The system log says:

ntpd_initres [5100]: ntpd returns a permission denied error!

What might be wrong and how can I fix it?

Thanks, JB

---

### Post by nemarasu on 2007-05-26
try running this from a terminal:

sudo /etc/init.d/ntp restart ; tail -f /var/log/messages

see if it starts correctly that way, or if it spits an error.

---

### Post by elspxvwcyr on 2007-05-26
Yes that worked, the time synced up fine, confirmed by messages in the system log. That doesn't look like a permanent fix, though.
JB

---

