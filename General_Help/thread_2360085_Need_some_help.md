---
title: "Need some help"
date: 2017-05-01
forum: General Help
---

### Post by morgro269 on 2017-05-01
Hi all.  Very new here and very new to Linux.  I need to write a bash script that will monitor a server for any changes to user accounts (added or deleted) and and email the changes.  The server should be checked a couple of times a day.  I'm thinking something along the lines a cron job that would run twice a day, run MD5 against the /etc/passwd file and if there is a change, somehow note the changes and email the changes.... Any help is greatly appreciated.

---

### Post by TheFu on 2017-05-02
User accounts are **not** just stored in the /etc/passwd file, BTW.

Why not just create a diff. If there is anything different, email those. If there aren't any differences, fine.

You also need to be clear about "any changes" - since some account data isn't stored in the password DB.  Some is stored in the shadow file and gshadow and some is stored in LDAP or other sorts of DBs.

If you just care about new/removed accounts, you'll want to strip out all the other stuff provided by the DB. Do you really care if someone changes their login shell?

Also, you could use inotify to watch for changes and trigger notification without cron involved, but I'd use an hourly cron myself unless there were thousands of users constantly changing things in the DB.

There are *beginning and advanced bash scripting guides*. Very useful. Full of good information. Google will find both.

As for the email part, you'll need to setup an MTA. Then just use Mail to send it where you like.
```
/path/to/run/script | Mail -s "Account Changes" you\@someplace.net
```
This assumes the script produces all desired output to stdout. That is a normal practice on Unix systems.

---

