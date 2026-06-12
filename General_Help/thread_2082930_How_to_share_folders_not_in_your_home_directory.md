---
title: "How to share folders not in your home directory"
date: 2012-11-10
forum: General Help
---

### Post by namoo on 2012-11-10
I've got a data drive mounted on my Ubuntu 12.04.  I've setup a samba and shared the mounted drive.  When I go to my windows machine, I can see the shared drive.  But cannot access it.

After trying to figure things out, I've found out that if I share a folder in my home directory, I am able to access it from the windows machine without problem.

Would anyone know what additional steps I need to perform in order to get this share to work.

Thanks in advance.

---

### Post by Morbius1 on 2012-11-11
Not enough information but it sounds like a Linux permissions issue not a Samba issue.

Please post the output of the following commands so we can see what method you are using to create the Samba share ( there are 2 ) and how they are set up:
```
testparm -s
``````
net usershare info --long
```

---

### Post by namoo on 2012-11-11
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Data Storage]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
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
    valid users = avahi, confluence, english, nobody, svn
    read only = No

[Data Storage]
    path = /media/Backup
    valid users = english
    read only = No


[Downloads]
path=/home/english/Downloads
comment=
usershare_acl=Everyone:F,
guest_ok=y

[My Pictures]
path=/media/Backup/My Pictures
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Data Storage]
path=/media/Backup
comment=
usershare_acl=Everyone:F,
guest_ok=y

---

### Post by Morbius1 on 2012-11-12
You have a couple of issues.

This is a Classic Samba Share. It's a private share allowing only one user access:
> [Data Storage]
    path = /media/Backup
    valid users = english
    read only = NoIn order for this to work "english" has to have access to /media/Backup itself and he has to have a samba password, as in:
```
sudo smbpasswd -a english
```You also have a Samba Usershare that you created through Nautilus of the exact same directory but this one allows anyone access. But, your guess is as good as mine as to which share definition Samba  will listen to so I would suggest getting rid of one or the other.  :
> [Data Storage]
path=/media/Backup
comment=
usershare_acl=Everyone:F,
guest_ok=y     In order for this one to work /media/Backup will have to have permissions of 777. If you want to use the Usershare then check to see if /media/Backup has permissions allowing "guest" ( i.e., a Linux "other" ) write access to the folder:
```
ls -dl /media/Backup
```[COLOR=Blue]*Note: This is redundant:*[/COLOR]
```
[My Pictures]
path=/media/Backup/My Pictures
comment=
usershare_acl=Everyone:F,
guest_ok=y

```Everyone that has access to /media/Backup share has access to all of it's subfolders.

---

