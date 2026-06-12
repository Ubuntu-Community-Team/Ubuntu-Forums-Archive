---
title: "CRON Default Directory"
date: 2008-02-07
forum: General Help
---

### Post by cmnorton on 2008-02-07
When using the system-wide cron table, one of the fields specifies the user name. When CRON executes the program, the user's login does not run. I did an empirical test, and CRON leaves the program at /. 

If you login to a remote system, doesn't the remote listener (ssh/telnet) authenticate you, run the shell, and then your login runs? Why doesn't CRON do this?

---

