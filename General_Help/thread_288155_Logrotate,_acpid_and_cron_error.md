---
title: "Logrotate, acpid and cron error"
date: 2006-10-29
forum: General Help
---

### Post by scarolan on 2006-10-29
I'm getting this error from an Ubuntu server running Dapper, inside a VMWare machine. Anyone have an idea what is causing it?  It comes in the cron email I get every week:

/etc/cron.daily/logrotate:
acpid: can't open /proc/acpi/event: Device or resource busy
error: error running postrotate script for /var/log/acpid
run-parts: /etc/cron.daily/logrotate exited with return code 1

---

