---
title: "X2Go error"
date: 2014-07-07
forum: General Help
---

### Post by martin114 on 2014-07-07
Hello, I have encountered this error second time in past week. First time I tried to restart Xubuntu but in never started again so I have to reinstall it.I was connected to my Xubuntu 14.04 dedicated server and then disconnected with "connection lost" error, when I tried to reconnect I got this error. Can anyone help me? I tried to search this error message with google but with no luck.

---

### Post by TheFu on 2014-07-07
The error says it is a read-only DB ... for SQLite, I'd guess that means the file system is mounted read-only or the DB is corrupt.
But I can't tell - these are just guesses.

Also, I have never used x2go - I'm not on 14.04 for my remote access systems yet, we still run FreeNX, but it is planned to migrate to x2go for later this month since FreeNX isn't alive anymore.

Hope it helps.  Might be worth looking at the log files too.

---

