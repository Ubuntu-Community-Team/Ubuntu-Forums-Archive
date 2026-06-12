---
title: "sarg help need"
date: 2008-01-03
forum: General Help
---

### Post by is13 on 2008-01-03
my script (via cron):

TODAY=$(date "+%d/%m/%Y")
/usr/bin/sarg -n -d $TODAY-$TODAY -c /etc/squid/sarg.hosts -l /var/log/squid/access.log

*** stack smashing detected ***: /usr/bin/sarg terminated

:confused:

Help me please...

(Ubuntu server 7.10, sarg_2.2.3.1-2ubuntu1)

---

### Post by reneerojas on 2008-01-31
helo there, i had the same problem with sarg, but looking around i find the problem!
every time when i put **LONG URL YES** at sarg.conf, this problem appear and sarg stop.
so, check this out and rebuild yours reports on sarg. :)

---

### Post by is13 on 2008-03-09
> **reneerojas said:**
> helo there, i had the same problem with sarg, but looking around i find the problem!
every time when i put **LONG URL YES** at sarg.conf, this problem appear and sarg stop.

cat /etc/squid/sarg.conf | grep long_url
# TAG: long_url yes|no
long_url no

:(

---

