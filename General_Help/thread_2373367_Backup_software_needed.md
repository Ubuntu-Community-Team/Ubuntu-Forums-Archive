---
title: "Backup software needed"
date: 2017-10-05
forum: General Help
---

### Post by panja on 2017-10-05
Hi all,

I'm pretty new to Ubuntu, well actually Linux in general.
Not a complete n00b but not that experienced.

I have an Ubuntu VPS running and I have an application that creates a ZIP file every night.
At home I have a Synology running and I would like to have that ZIP file (and some other files as well) backupped to my Synology.
But I would like to set a retention. So after let's say 7 days, the old files will get deleted. So I have 7 versions, not more.
The files do NOT need to be compressed, I want a 1on1 copy on my Synology.

What software would suit my needs?
I prefer an app with a GUI.

---

### Post by TheFu on 2017-10-05
Most VPS don't run GUIs. Also, a GUI tool is harder (impossible?) to automate/schedule in cron.  I'd forgetaboutit.

Make the ZIP file have a date-tag in the name and use rsync/grsync.  Then you can remove the files using a local script on the Synology.  I would keep 60 days, myself.  A VPS isn't exactly low-risk.  For my high-risk servers, I keep 120 days of versioned backups.

Backup software really isn't for 1 file.  It is to get a set of directories or the entire system.  I use rdiff-backup, but duplicity, and a few others are viable alternatives.  

IMHO.

BTW, rather than doing the ZIP process, why not just have your backup tool get the source files directly?  Srsly.

---

### Post by panja on 2017-10-05
Thanks, I'll have a look.

---

