---
title: "Error-mails"
date: 2005-04-25
forum: General Help
---

### Post by mikl on 2005-04-25
I am a happy new convert of (K)ubuntu, and I am really enjoying this fine distribution.

However, I seem to get two automated error-mails in /var/mail/ every day, and I have no real idea on how to fix the issues, or whether I should just ignore them.
Firstly, and most urgent is this:
```
/usr/bin/mysqlcheck: Got error: 1045: Access denied for user: 'debian-sys-maint@localhost' (Using password: YES) when trying to connect

 Improperly closed tables are also reported if clients are accessing
 the tables *now*. A list of current connections is below.
```
I also get something like this when shutting down. After changing to ubuntu (from gentoo), I just copied over the contents of /var/lib/mysql/ from my old install, overwriting whatever might have been there installed by apt.
So I obviosly need to enable passwordless-login for the system to mysql. How to do this?

Next is this I get from anacron:
```
/etc/cron.daily/logrotate:
error: error running shared postrotate script for /var/log/mysql.log /var/log/mysql/mysql.log /var/log/mysql.err /var/log/mysql/mysql.err /var/log/mysql/mysql-slow.log 
run-parts: /etc/cron.daily/logrotate exited with return code 1
/etc/cron.daily/man-db:
mandb: warning: /usr/share/man/man1/x-terminal-emulator.1.gz is a dangling symlink
```
I have no good ideas on this one, however. Any kind of help will be appreciated.

---

### Post by BKonkle on 2006-05-04
I'm having the second problem that the previous poster described with a fresh install of Ubuntu 5.10 in headless server mode.  Anyone have any ideas what the situation is?

---

### Post by BKonkle on 2006-05-04
I'm actually getting both emails now.  Anyone have any information for us?

---

### Post by Ribs on 2006-08-18
Have you done what I've done and restored an old mysql database? I'm not sure if this is what has caused this for me, but I feel it's the most likley cause.

Be carefull when importing databases. Debian/Ubuntu expects a user to be present on the mysql system at all times for the purposes of checking, upgrading and logrotation. If this user is not present, then scripts such as the logrotate and mysqlcheck will fail.

The user is debian-sys-maint. The password is randomly generated (I think). Check your /etc/mysql/debian.cnf file for the password.

Creating this user (with full permissions and the right password, of course) should fix the problem. I'll find out myself tonight :)

---

### Post by Ribs on 2006-08-20
> **Ribs said:**
> Creating this user (with full permissions and the right password, of course) should fix the problem. I'll find out myself tonight :)

This did indeed fix the issue. I no longer see error e-mails about this.

---

