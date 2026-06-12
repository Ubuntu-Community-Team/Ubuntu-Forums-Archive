---
title: "Remastersys login problems pswd fail help"
date: 2014-09-15
forum: General Help
---

### Post by einstein**-7 on 2014-09-15
Hey, I'm trying to backup a 12.04 Ubuntu sys that is heavily customized so that I can rebuild the sys quickly after hardware changes.
The remastersys builds the sys with no probs but when running the ISO either with virtual box or bootable USB on the same physical machine the login paswd of " custom " fails..
Need help with checking user ID num's and disabling auto login the the guest account.. 
Thanks in advance&#9786;

---

### Post by einstein**-7 on 2014-09-16
I just attached a pic of the Casper.log file same for VM or USB.
First error is for user ID 999 in use but when I search for that user on the host system no user has that ID?
Also tried to register on the remastersys forum and can't get it tot work just a mysterious error no reasons??
Thanks

---

### Post by yancek on 2014-09-16
If you used the 'Dist' option which will not include your /home directory, the default user is 'custom' and there is not password.  I've always used this method and this was always the case.
If you used the 'Backup' method including your /home directory then it is the user name and password from the original install.

---

