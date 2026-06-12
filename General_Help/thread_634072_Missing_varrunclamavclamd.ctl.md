---
title: "Missing /var/run/clamav/clamd.ctl"
date: 2007-12-07
forum: General Help
---

### Post by btaylor101 on 2007-12-07
I attempted to run the command sudo freshclam and received the message
> ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).

So I checked the log and see this entry

> daily.inc updated (version: 5028, sigs: 39879, f-level: 21, builder: ccordes)
Database updated (173042 signatures) from db.local.clamav.net (IP: 64.246.134.133)
WARNING: Clamd was NOT notified: Can't connect to clamd through /var/run/clamav/clamd.ctl

It looks like the system is updating, but not connecting to clamd.ctl. I went into the run directory and saw that there is no /clamav/clamd.ctl

This brought up two questions.
1) What is clamd.ctl
2) What do I need to put into the clamd.ctl

---

### Post by milhafre on 2007-12-21
I'm having the same problem, i need help too.

---

### Post by BigBob on 2008-02-08
Hi,

sudo apt-get install clamav-daemon

A++

---

