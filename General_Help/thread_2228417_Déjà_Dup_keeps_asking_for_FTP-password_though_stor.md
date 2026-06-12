---
title: "Déjà Dup keeps asking for FTP-password though stored [Ubuntu 14.04]"
date: 2014-06-07
forum: General Help
---

### Post by a.borque on 2014-06-07
Hello!
I am using Déjà Dup to create backups on my NAS using FTP. 
This worked without any problems for a very long time, but recently Déjà Dup started aksing me for the password for the FTP-account whenever it starts a backup-task, though I have checked the option to remeber the password. 
Of course the password is correct and I have also already checked that it is stored correctly in the keyring. I have even tried to delete the entry in the keyring and recreated it.
I can not say for sure, but it might have starte after upgrading from 12.04 to 14.04.
Any suggestions / help?
Thanks!
A.Borque

---

### Post by a.borque on 2014-06-08
Okay I hace found the problem. Deja Dup stored the password in a seperated section of the keyring (I don't know why). Moving them to the main section everything works fine now.

---

