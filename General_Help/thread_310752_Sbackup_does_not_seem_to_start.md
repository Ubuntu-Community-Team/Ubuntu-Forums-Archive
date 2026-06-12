---
title: "Sbackup does not seem to start"
date: 2006-12-01
forum: General Help
---

### Post by CameronCalver on 2006-12-01
Hello i have a Maxtor 300gb external harddrive which i would like to backup some folders totaling 10gb i used sbackup.
I set the include folders and the exclude folders in a manual backup and clicked backup.
It said it started process ..... but it does not seem to be doing anything am i missing something out here

---

### Post by rjh78 on 2006-12-15
I had the same problem.  I ran the sbackupd process as root from the terminal, and found that sbackup was trying backup something from an NFS share from which it did not have permissions (odd being that its running as root).  

All I did was exclude that folder from the backup and it worked :-)

---

