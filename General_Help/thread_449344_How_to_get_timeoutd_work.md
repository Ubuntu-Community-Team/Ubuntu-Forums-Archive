---
title: "How to get timeoutd work"
date: 2007-05-20
forum: General Help
---

### Post by hannur on 2007-05-20
I need to limit one user computing time, and I have tried to get timeoutd working.
I need to mention that I'm a newbie in Linux world. 
Anyway here is timeouts- file where henkka is a user who gets 120 min time per day to use computer.
Is there something i have not understand or haven't noticed.

```
# /etc/timeouts: user login/idle/session time limits.  See timeouts(5).
#
# Format:  TIMES:TTYS:USERS:GROUPS:MAXIDLE:MAXSESS:MAXDAY:WARN
#   or:    TIMES:TTYS:USERS:GROUPS:LOGINSTATUS
#
# Some examples:
#
# dopey is not allowed to login
#Al:*:dopey:*:NOLOGIN
#
# cas gets unlimited use
#Al:*:cas:*:0:0:0:0
#
# fred is allowed 20 minutes idle, 240 mins per session, and 480 mins per day
# on ttyS3
#Al:ttyS3:fred:*:20:240:480:10
#
# everyone else is allowed only 120min/session, 240/day
#Al:ttyS3:*:*:20:120:240:5
#
[B]# henkka is allowed 120 mins per day
Al:*:henkka:*:120:5
```[/B]

---

