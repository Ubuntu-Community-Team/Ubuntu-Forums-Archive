---
title: "Mysterious System Restarts"
date: 2008-03-21
forum: General Help
---

### Post by dmitriyp13 on 2008-03-21
Over the past few weeks I have noticed that when I return to my computer in the morning, instead of getting the screen saver password prompt, I get the regular log in screen.  After looking at a few logs, I found my first clue in /var/log/messages
```
Mar 21 07:40:08 bohr syslogd 1.4.1#21ubuntu3: restart.
```
Looking at /var/log/syslog reveals
```

Mar 21 07:38:14 bohr syslogd 1.4.1#21ubuntu3: restart.
Mar 21 07:38:14 bohr anacron[8110]: Job `cron.daily' terminated
Mar 21 07:40:01 bohr anacron[8110]: Job `cron.weekly' started
Mar 21 07:40:01 bohr anacron[8301]: Updated timestamp for job `cron.weekly' to 2008-03-21
Mar 21 07:40:08 bohr syslogd 1.4.1#21ubuntu3: restart.
Mar 21 07:40:08 bohr anacron[8110]: Job `cron.weekly' terminated
Mar 21 07:40:08 bohr anacron[8110]: Normal exit (2 jobs run)

```
Not particularly helpful.  My second clue comes from /var/log/auth.log
```

ar 21 07:40:02 bohr su[8321]: Successful su for nobody by root
Mar 21 07:40:02 bohr su[8321]: + ??? root:nobody
Mar 21 07:40:02 bohr su[8321]: pam_unix(su:session): session opened for user nobody by (uid=0)
Mar 21 07:40:07 bohr su[8321]: pam_unix(su:session): session closed for user nobody

```
I am not an expert on normal maintenance operations in Ubuntu so perhaps the above is normal.  Can someone shed light on this?

---

### Post by dmitriyp13 on 2008-03-31
bump...

Has anyone else seen this?

---

