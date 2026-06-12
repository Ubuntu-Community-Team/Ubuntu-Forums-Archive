---
title: "PRUNEPATHS in updatedb.conf does not work"
date: 2007-08-13
forum: General Help
---

### Post by surfer63 on 2007-08-13
Hi,

I'm using dirvish as a backup mechanism. I create a backup directory on my data partition (/data), e.g. /data/backup. I don't want updatedb to index this path so I changed my updatedb.conf and changed the default PRUNEPATHS line to: 
PRUNEPATHS="/tmp /usr/tmp /var/tmp /afs /amd /alex /var/spool /sfs /media /data/backup"

However, this does not work. The other ones are pruned but not /data/backup. 

What is wrong here?

---

