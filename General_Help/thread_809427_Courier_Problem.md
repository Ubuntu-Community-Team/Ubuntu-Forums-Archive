---
title: "Courier Problem"
date: 2008-05-27
forum: General Help
---

### Post by Black Mage on 2008-05-27
I am currently having a problem with courier, and I could not figure it out so I set my log reporting an in authdaemon to level 2, and I got this back

Error Log:
May 27 11:52:56 mainserver courierpop3login: Connection, ip=[::ffff:127.0.0.1]
May 27 11:53:04 mainserver authdaemond: received auth request, service=pop3, authtype=login
May 27 11:53:04 mainserver authdaemond: authmysql: trying this module
May 27 11:53:04 mainserver authdaemond: SQL query: SELECT id, "", clear, uid, gid, home, concat(home,'/',maildir), "", name, "" FROM users WHERE id = "ddixon" AND (enabled=1)
May 27 11:53:04 mainserver authdaemond: zero rows returned
May 27 11:53:04 mainserver authdaemond: no password available to compare
May 27 11:53:04 mainserver authdaemond: authmysql: REJECT - try next module
May 27 11:53:04 mainserver authdaemond: FAIL, all modules rejected
May 27 11:53:04 mainserver courierpop3login: LOGIN FAILED, user=ddixon, ip=[::ffff:127.0.0.1]
May 27 11:53:20 mainserver courierpop3login: LOGOUT, ip=[::ffff:127.0.0.1]
May 27 11:53:20 mainserver courierpop3login: Disconnected, ip=[::ffff:127.0.0.1]



It seems its trying to connect to a mysql database but I never configured it to connect to a database. So what should I do to try and fix this?

Thanks

---

