---
title: "Samba wont let me access folder"
date: 2013-10-15
forum: General Help
---

### Post by zaoka on 2013-10-15
I have the same user added to Samba and to Linux with the same password.

authentication = user
valid users = me

Shared folder is set to be CHMOD 777

I go to Windows machine that is using different username and password to login to windows, however, when accessing that shared folder I supply linux username and password and it wont let me access.

Does this means that in order to access that shared folder my Windows machine also need to have the same username and the same password?

 If that is true, how can I make Samba to let me access shared folder from different windows accounts?

---

### Post by Morbius1 on 2013-10-16
> valid users = me
Did you literally add that option to your share definition?

Samba doesn't know anything about the user "me". That's a silly thing that Nautilus does.

You need to replace "me" with the real user name.

---

### Post by zaoka on 2013-10-16
Of course that I used real name :)

---

### Post by Morbius1 on 2013-10-16
Please post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by zaoka on 2013-10-16
```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[temp]"
Processing section "[read]"
Processing section "[ays]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:                * %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb
        hosts allow = 192.168.1.1/24
        browseable = No

[homes]
        comment = Home Directories
        invalid users = gost
  read only = No

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        print ok = Yes

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
        browseable = Yes

[temp]
        comment = Temp folder za sve da mogu da rade sta hoce
        path = /temp
        read only = No
        create mask = 07777
        directory mask = 07777
        guest ok = Yes
        browseable = Yes

[read]
        comment = Folder samo za preuzimanje informacija
        path = /read
        create mask = 00
        directory mask = 00
        guest ok = Yes
        browseable = Yes

[ays]
        comment = Folder samo za ays grupu i za ays bekap
        path = /ays
        valid users = ays
        read only = No
        browseable = Yes
```

---

### Post by zaoka on 2013-10-16
Your second command does nothing, no output.

---

### Post by zaoka on 2013-10-16
So the problem is to access ***ays*** folder, others works OK.

I want to be able to access that folder from any Windows PC by entering Linux login info for ays user and I dont want to have Windows machine with the same user and password to be able to access that folder.

---

### Post by Morbius1 on 2013-10-16
What are the permissions on the shared folder:
```
ls -dl /ays
```

---

### Post by zaoka on 2013-10-16
Its fixed. My Windows 7  was set for Public Networks, I changed to Home Networks and its working fine.

maybe its better this way, i leaned a lot about Samba :)

Thanks man!!!!!!

---

