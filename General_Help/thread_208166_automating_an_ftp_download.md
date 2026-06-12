---
title: "automating an ftp download"
date: 2006-07-03
forum: General Help
---

### Post by hairshirt on 2006-07-03
Is there a way I could automate an ftp download and download from a Wind0zs Web Server (2oo3).  I have Backup4all running on the server that creates a backup of the server at 02:00 and I would like to automatically download that backup soon after to a linux machine.  All while I sleep.

It's the only Wind0zs Server I manage.  The client insisted upon it and in any case the client site is running under *.asp.

PS. Just for interest...  Has anyone managed to get an *.asp and M$SQL site running under Linux or FreeBSD?

Many thanks in advance, Mark.

PPS. And, of course, if you can and I'm sure it's possible, how would I go about it.

---

### Post by halfvolle melk on 2006-07-03
What I'd try is using cron and lftp or any other cli-ftp-client. The script would look something like this:
```
#!/bin/bash
lftp -c -p 21 -u usr,passwd 1.2.3.4; mirror -R /remote/source/ ~/local/target/
```
and let cron run it at 02:00.
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

Something along those lines anyway. Good luck.

---

