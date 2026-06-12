---
title: "Grsync not getting permission to destination drive on add-wrt router NAS"
date: 2017-01-25
forum: General Help
---

### Post by waltd on 2017-01-25
Hi all,
    I have a NAS, USB drive connected to my dd-wrt wifi router.  When I manually access the drive it works fine, no problem.    
    However, when I try to create a backup on this drive using grsync I get this error message from grsync saying "Permission denied".  I have the "run as superuser" option checked in the extra options tab.  Can someone help me this fix this problem to have grsync access this drive?  Below is the error message from grsync.  Thanks. 
       
    rsync: ERROR: cannot stat destination "/run/user/1000/gvfs/smb-share:server=dd-wrt,share=ddwrtdrive/": Permission denied (13)rsync error: errors selecting input/output files, dirs (code 3) at main.c(652) [Receiver=3.1.1]
Rsync process exit status: 3

---

### Post by waltd on 2017-01-25
I found the cause of the problem.  I had to uncheck the "run as superuser" option.

---

