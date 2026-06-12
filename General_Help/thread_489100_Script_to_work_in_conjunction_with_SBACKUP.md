---
title: "Script to work in conjunction with SBACKUP"
date: 2007-07-01
forum: General Help
---

### Post by jconnett on 2007-07-01
I have a question regarding scripting.  I use SBACKUP and it has saved my bacon more than once.  I have it set to do a full backup once every 28 days and incrementals every day inbetween.  I have been using the GUI to simply take the first FULL backup and the next 28 INCREMENTAL backups up to the next full backup and archiving them in a .zip file.  I'd like to use the command line or a script to do that.

Basically, the script should ask for the file name where I'd like to begin (the full backup) and then automatically take all files in succession (by date) up to one day before the next full backup and zip them into one file.

It would be much easier for me to do this from the command line rather than via GUI.

Any ideas?

--Jim

---

