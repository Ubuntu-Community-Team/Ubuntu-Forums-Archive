---
title: "CUPS Job Permissions"
date: 2013-10-26
forum: General Help
---

### Post by lee_connell on 2013-10-26
I have installed cups 1.6, I can see the logs show when I send a print job, however in the /var/spool/cups/ directory my print jobs are only given access to the root user and nobody else, hence I am seeing an error in my logs saying "permission denied" when cups tries to read the job for printing.  I can't seem to find anywhere in the cupsd.conf to set those permissions for new jobs.  It looks as if the user lpr is trying to access the job that was only given permissions to user "root".

Any assistance would be appreciated. thanks!

---

