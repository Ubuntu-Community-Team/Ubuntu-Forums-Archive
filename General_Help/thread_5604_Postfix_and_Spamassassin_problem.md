---
title: "Postfix and Spamassassin problem?"
date: 2004-11-20
forum: General Help
---

### Post by ubuntuthebest on 2004-11-20
Hi,

Sorry, my English is not good (translated) can me someone help? :(

Postfix and Spamc

```
Nov 20 15:12:18 ubuntu postfix/postfix-script: fatal: the Postfix mail system is not running
Nov 20 15:13:28 ubuntu postfix/postfix-script: fatal: the Postfix mail system is not running
Nov 20 14:13:28 ubuntu postfix/postqueue[3343]: fatal: Cannot flush mail queue - mail system is down
Nov 20 15:13:37 ubuntu postfix/postfix-script: starting the Postfix mail system
Nov 20 15:13:37 ubuntu postfix/master[3648]: daemon started -- version 2.1.3
Nov 20 15:13:39 ubuntu spamd[3345]: server started on port 783/tcp (running version 2.63)
Nov 20 15:22:41 ubuntu spamc[4437]: connect(AF_INET) to spamd at 127.0.0.1 failed, retrying (#1 of 3): Connection refused
Nov 20 15:22:42 ubuntu spamc[4437]: connect(AF_INET) to spamd at 127.0.0.1 failed, retrying (#2 of 3): Connection refused
Nov 20 15:22:43 ubuntu spamc[4437]: connect(AF_INET) to spamd at 127.0.0.1 failed, retrying (#3 of 3): Connection refused
Nov 20 15:22:44 ubuntu spamc[4437]: connection attempt to spamd aborted after 3 retries
Nov 20 15:22:46 ubuntu spamd[4440]: server started on port 7830/tcp (running version 2.63)
Nov 20 15:22:46 ubuntu spamd[4440]: connection from localhost.localdomain [127.0.0.1] at port 32975
Nov 20 15:22:46 ubuntu spamd[4442]: processing message (unknown) for pero:1000.
Nov 20 15:22:46 ubuntu spamd[4442]: clean message (3.1/5.0) for pero:1000 in 0.3 seconds, 19 bytes.
Nov 20 15:22:46 ubuntu spamd[4440]: connection from localhost.localdomain [127.0.0.1] at port 32976
Nov 20 15:22:46 ubuntu spamd[4444]: checking message <1100960218.4239.0.camel@ubuntu> for pero:1000.
Nov 20 15:22:46 ubuntu spamd[4444]: clean message (0.0/5.0) for pero:1000 in 0.2 seconds, 806 bytes.

```

Thanks ahead

---

### Post by ubuntuthebest on 2004-11-21
??? :confused:

---

