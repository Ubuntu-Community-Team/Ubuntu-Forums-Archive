---
title: "Samba, public and private shares"
date: 2013-01-29
forum: General Help
---

### Post by zombie8u on 2013-01-29
Is there any way to set up public shares and private shares? I have my public shares setup and working so that anyone can read and write without needing a password. I would like to set up a share that requires a username and password to read and write to. I'm using Ubuntu 12.04

---

### Post by xianbei on 2013-01-29
8u,

Does this help?

[http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html](http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html)

Cheers.

---

### Post by Morbius1 on 2013-01-30
You didn't state what method you are using to create the samba shares - there are 2: One is created in Nautilus and the other is in smb.conf itself.

I'm guessing that had you used Nautilus it would be obvious since you would have checked only 2 of the 3 boxes to make a private share ( see attachment ).

To create a private share in smb.conf in it's simplest form:
> [share-name]
path = /path/to/folder
guest ok = no
read only = no[I][COLOR=Blue]Note: There are an infinite number of variations of that type of share definition depending on how you want to control who can do what.[/COLOR]
[/I]
In either method you will need to create a user on your Linux box representing each LAN user and then you have to add them to the samba password database. So if you have a remote user named morbius:

** Create a user morbius on your Linux box.
** Add him to the samba database using this command:
```
sudo smbpasswd -a morbius
```

---

### Post by zombie8u on 2013-01-30
Thanks for the replies. 

I used the smb.conf method to create the shares.

Morbius1
Your suggestion did give me the password prompt that I was wanting, but I didn't have the permission to write to it, also once I entered my username and password I  lost the permission to write to my public share.

thanks.

---

### Post by Morbius1 on 2013-01-30
Please post the output of the following command:
```
testparm -s
```

---

### Post by zombie8u on 2013-01-30
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[share]"
Processing section "[backup]"
Processing section "[PRIVATE]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = ALB_GROUP
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[share]
    comment = backup share
    path = /srv/samba/share
    read only = No
    create mask = 0755
    guest ok = Yes

[backup]
    comment = backup dir
    path = /home/misty/backup
    read only = No
    create mask = 0755
    guest ok = Yes

[PRIVATE]
    path = /srv/samba/private
    read only = No

---

### Post by Morbius1 on 2013-01-30
And the output of this one please:
```
ls -al /srv/samba
```

---

### Post by Rebelli0us on 2013-01-30
"Samba Server Configuration" (system-config-samba)  lets you create shares and specify access only to individual users **or** "allow access to everyone".

---

### Post by Morbius1 on 2013-01-30
> **Rebelli0us said:**
> "Samba Server Configuration" (system-config-samba)  lets you create shares and specify access only to individual users **or** "allow access to everyone".
The shares have already been created. The only issue left now is Linux  permissions. That is something nautilus-shares modifies automatically  whereas system-config-samba does not. So your post is a non sequitur.

---

### Post by zombie8u on 2013-01-30
total 16
drwxr-xr-x 4 root   root    4096 Jan 30 08:36 .
drwxr-xr-x 3 root   root    4096 Jan 24 13:44 ..
drwxr-xr-x 2 root   root    4096 Jan 30 08:36 private
drwxr-xr-x 2 nobody nogroup 4096 Jan 30 10:47 share

---

### Post by Morbius1 on 2013-01-30
You have 2 options:

[1] Change permissions on the directories themselves to allow everyone access and then use Samba to control who has access:
```
sudo chmod 0777 /srv/samba/share
sudo chmod 0777 /srv/samba/private
```[2] This is more compliated but change the share definitions, permissions, and group membership:

Change the [share] to this:
> [share]
    comment = backup share
    path = /srv/samba/share
    read only = No
    create mask = 0755
    guest ok = Yes
[COLOR=Blue]**force user = nobody**[/COLOR]Change [private] to this:
> [PRIVATE]
path = /srv/samba/private
guest ok = no
read only = no
[COLOR=Blue]**force group = plugdev**[/COLOR]Change ownership to this:
```
sudo chown :plugdev /srv/samba/private
```Change permissions to this:
```
 sudo chmod 0775 /srv/samba/private
```And then add your remote user to the plugdev group:
```
sudo gpasswd -a morbius plugdev
```You will have to logout and back again for the group membership to take affect.

---

### Post by zombie8u on 2013-01-31
Morbius1

I did your second suggestion and was able to get permission to write to the public share after entering username and password for the private share, but still do not have write permission to the private share.

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[share]"
Processing section "[backup]"
Processing section "[private]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = ALB_GROUP
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[share]
    comment = backup share
    path = /srv/samba/share
    force user = nobody
    read only = No
    create mask = 0755
    guest ok = Yes

[backup]
    comment = backup dir
    path = /home/misty/backup
    valid users = misty
    read only = No
    create mask = 0755

[private]
    path = /srv/samba/private
    valid users = misty
    force group = plugdev
    read only = No

``````
total 16
drwxr-xr-x 4 root   root    4096 Jan 30 08:36 .
drwxr-xr-x 3 root   root    4096 Jan 24 13:44 ..
drwxr-xr-x 2 root   plugdev 4096 Jan 30 08:36 private
drwxr-xr-x 2 nobody nogroup 4096 Jan 31 08:21 share

```

---

### Post by Morbius1 on 2013-01-31
> but still do not have write permission to the private share.You missed a step. Assuming "misty" is a member of the plugdev group your folder still doesn't allow a write to that group:

> drwxr-xr-x 2 root   plugdev 4096 Jan 30 08:36 privateChange it:
```
sudo chmod 0775 /srv/samba/private
```Another Alternative: If the only user that you want to grant access to the share is misty then change ownership of the folder to misty:
```
sudo chown misty:plugdev /srv/samba/private
```

---

### Post by zombie8u on 2013-01-31
Morbius1

That worked perfectly. You really know your stuff.

I can't thank you enough for the help you have given me.

---

