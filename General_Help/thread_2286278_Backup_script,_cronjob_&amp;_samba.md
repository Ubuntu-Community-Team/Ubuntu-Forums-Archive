---
title: "Backup script, cronjob &amp; samba"
date: 2015-07-11
forum: General Help
---

### Post by vangend.robert on 2015-07-11
We have Ubuntu 12.04 server running on a machine. This is our data server. We have several Windows 7 clients running. I have two external USB drives in one of the client machines, and we have all the machines running on a Samba network.
I have written a backup script to backup all server data once a week onto one of the USB external drivers (full back – level 0). Every other day of the week, the same script runs and write a differential backup to the other USB drive.
When I run the script from the command line, it works fine.
I have created a cronjob to run the script automatically every night at 00:05. However, whenever the scrip runs automatically, the backup freezes.
In the script I have several source locations on the dataserver (i.e. company public data is one source, company private data is another source, and so on…). I write each source location to a different tar file on the target, depending on the day of the week, this will either be a full or a differential backup.
I read something about a samba “bug” in samba, but I cannot found that link, and I am not sure if this is the actual cause of the problem.
Does anyone have any ideas?

I have attached the script in case this is of any use.

---

