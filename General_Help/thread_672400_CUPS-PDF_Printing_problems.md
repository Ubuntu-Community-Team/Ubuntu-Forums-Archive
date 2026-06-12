---
title: "CUPS-PDF Printing problems"
date: 2008-01-19
forum: General Help
---

### Post by davjutz on 2008-01-19
Hi
I have had problems printing to pdf since i change the output directory
could someone please tell me if i changed the wrong thing, I would like to have all users who print stuff through pdf go to my storage user's desktop where i keep all my files

I also restarted cups (/etc/init.d/cupsys restart) afterwords too to try and see if that worked but it didn't

Here's a copy of what i had changed
### Key: Out
##  CUPS-PDF output directory 
##  special qualifiers: 
##     ${HOME} will be expanded to the user's home directory
##     ${USER} will be expanded to the user name
##  in case it is an NFS export make sure it is exported without
##  root_squash! 
### Default: /var/spool/cups-pdf/${USER}

Out /home/storage/Desktop/PDF

---

