---
title: "Can't backup Ubuntu 14.04 data on an unRAID server"
date: 2014-11-22
forum: General Help
---

### Post by loren41 on 2014-11-22
I had been using Backups (Duplicity) to backup data files from my Ubuntu 14.04 and send them to a Windows share  on my home network unRAID server.  A  recent crash forced me to recover about 500Gb of storage.  Unfortunately, I learned that I had backed up very large folders using multiple incremental files.  I could not identify specific data in the backups and learned that my Thunderbird files were badly scrambled.  My own limited knowledge did little help.  I recovered as much data as I could and my pc is now back to normal.

Internet research suggests many Linux backup solutions, but I don't want to use the Command Line and need to move the backups to my server and recover them easily if needed.  Currently I am testing Back In Time and like the interface.  Unfortunately t am experiencing problems with unsupported symbolic links via Samba and wonder if I need Samba at all.   Can anyone suggest a gui-based solution?

---

### Post by loren41 on 2014-11-24
Ok, nothing but silence out there.  I must not be asking a clear question.  Hypothetically, all Ubuntu users are backing up their data on a regular basis.  Therefore, they must be using some tool to do this.  Perhaps they are using rsync with a companion gui interface.  I am trying to move the backups to a samba share on my home server.  I don't want to use cloud storage.  What are you good Ubuntu folks using?

---

