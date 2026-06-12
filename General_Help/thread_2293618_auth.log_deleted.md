---
title: "auth.log deleted"
date: 2015-09-06
forum: General Help
---

### Post by safeguard982-bri on 2015-09-06
Hi guys,

when exactly is the auth.log deleted / recreated? And is there a way to store it longer? I had entries for the last few days and today the log was cleared. 

thanks

---

### Post by Lars Noodén on 2015-09-06
The old log gets rotated to auth.log.1 and then rotated + compressed to auth.log.2.gz and up.

The configuration file /etc/logrotate.d/rsyslog contains the rotation settings.  See the manual page for [logrotate](http://manpages.ubuntu.com/manpages/trusty/en/man8/logrotate.8.html) for all the details of what goes on.

---

### Post by safeguard982-bri on 2015-09-06
> **Lars Noodén said:**
> The old log gets rotated to auth.log.1 and then rotated + compressed to auth.log.2.gz and up.

The configuration file /etc/logrotate.d/rsyslog contains the rotation settings.  See the manual page for [logrotate]("http://manpages.ubuntu.com/manpages/trusty/en/man8/logrotate.8.html") for all the details of what goes on.

That makes sense of course :)
Thank you!

---

