---
title: "Backup problems with sbackup and backup-manager"
date: 2007-02-01
forum: General Help
---

### Post by danzinho on 2007-02-01
Hi

I've been trying two different solutions for backup but neither of them seems to work satisfactorily.

sbackup
-----------
This looks great.  Configuration appears simple.  When I set everything up and do 'Backup Now' it goes ahead and does it.  *However*, it doesn't go ahead and do all the daily backups.  Other people seem to have seen this.  Has anyone found a solution?

backup-manager
------------------------
A bit harder to set up, but has the advantage of doing the FTP onto another machine too.  The problem here is that it doesn't seem to obey the intended timings on making master backups and incremental ones.  I ask for a master backup once a week but it hasn't made one in a month.  In fact, I'm not sure the incremental ones are working right either - it's writing ~700M per day.  I work hard but not that hard :) 

Thanks in advance for advice on these, or suggestions of alternatives.

Daniel

---

### Post by glabouni on 2007-02-01
you can read this: [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

[http://ubuntu-tutorials.com/2006/05/23/backup-and-recovery/](http://ubuntu-tutorials.com/2006/05/23/backup-and-recovery/)

---

