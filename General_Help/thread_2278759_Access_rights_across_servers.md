---
title: "Access rights across servers"
date: 2015-05-18
forum: General Help
---

### Post by ylafont on 2015-05-18
[FONT=Helvetica Neue]I need some tutelage on the rights across unix. I could swear this has never been a problem but for some reason something is failing.[/FONT]
[FONT=Helvetica Neue]On a NAS there is media share. I have set the permissions to 777 on the share to avoid potential issues.
[/FONT]
[FONT=Helvetica Neue]On a client I mount that share via FSTAB[/FONT]
[FONT=Helvetica Neue]
//192.168.1.2/root /mnt/NasOne cifs username=USER1,password=PASS1,sec=ntlm,_netdev 0 0[/FONT]
[FONT=Helvetica Neue]
The share mounts fine, however I get permission denied when i try to create a file. although the directory rights are listed as drwxrwxrwx for the folder.

If I perform a ls > a.txt  on the client, the file is created with a user and group of 98.  list the file on the NAS, it is reported and to have user and group of admin.
[/FONT]
[FONT=Helvetica Neue]As a test, I have created a users with the same name on the NAS and placed him in the sudo group and mounted the share as that user. but that made no difference[/FONT]
[FONT=Helvetica Neue]
What i am missing?[/FONT]

---

