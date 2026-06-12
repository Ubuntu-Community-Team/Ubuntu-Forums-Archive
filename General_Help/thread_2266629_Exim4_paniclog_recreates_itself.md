---
title: "Exim4 paniclog recreates itself"
date: 2015-02-24
forum: General Help
---

### Post by lordbah2 on 2015-02-24
Every day I receive email that the mail system may be broken because paniclog is not empty. (It's not broken, it's fine other than this message)
If I 'touch paniclog', the next day the message arrives again, and sure enough those same lines are back in paniclog. The entries are from a month ago now but they keep coming back. These strings do not occur anywhere under /var/log, I don't know where exim4 is collecting them from.

2015-01-24 16:47:39 1YF8Vv-00069J-UG spam acl condition: error reading from spamd socket: Connection timed out
2015-01-24 16:49:50 1YF8Vv-00069J-UG spam acl condition: error reading from spamd socket: Connection timed out
2015-01-24 17:28:19 1YF99c-0006DJ-SX spam acl condition: error reading from spamd socket: Connection timed out
...

Every day it's those same lines from January 24th, NOT new lines every day. Whatever the original problem was connecting to spamd, it's not a problem any more. Those lines aren't something in memory since I've rebooted a few times since then. Before I go 'grep -r' the whole bloody disk, can someone tell me where it might be finding these lines?

---

