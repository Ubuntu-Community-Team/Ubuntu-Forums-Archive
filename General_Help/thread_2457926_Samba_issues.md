---
title: "Samba issues"
date: 2021-02-12
forum: General Help
---

### Post by genje on 2021-02-12
[FONT=verdana]I've been struggling to share a directory in Ubuntu-Server 20.04 with my Windows machine using samba. The directory is located at /mnt/share. I am using mergerfs to pool my drives in this folder. I have no other users on the network, so I am not too concerned with security on my LAN.[/FONT]
[FONT=verdana]No matter what options I have used in smb.conf, whenever I tried to write to the share, I would receive the message in Windows: "You need permission to perform this action"
[/FONT]
[FONT=verdana]I've looked up many guides and forum posts on configuring samba, each guide telling me to do something different. The only way that has worked for me was running chown -R nobody /mnt/share, and having the options in smb.conf:
[/FONT]
[FONT=verdana]writeable = yes[/FONT]
[FONT=verdana]browseable = yes[/FONT]
[FONT=verdana]read only = no[/FONT]
[FONT=verdana]guest ok = yes[/FONT]
[FONT=verdana]create mask = 0777[/FONT]
[FONT=verdana]directory mask = 0777[/FONT]
[FONT=verdana]force user = nobody
[/FONT]
[FONT=verdana]But I was wondering what the implications of setting the directory ownership, (and all the files underneath this directory) to nobody, and if there is a better way to go about this.[/FONT]

---

### Post by dinkidonk on 2021-02-13
Have you created an account for the samba shares?

```
#create user with no home and no local login
sudo adduser --no-create-home --disabled-password --disabled-login the_user_name

#create a samba password for the user
sudo smbpasswd -a the_user_name
```

Make sure that the user has local read/write access to the shared folder(s). In you smb.conf file let the created user be the owner of the shares (and disable guests, pls).

Not being concerned about security is a stupid standpoint.

---

### Post by mikewhatever on 2021-02-13
If you want to modify files in a directory as the user "nobody", that directory has to be readable/writable by "nobody". There is no way to do it without having permission to. ...not sure why it is surprising.
The implications are being able to modify files.

---

