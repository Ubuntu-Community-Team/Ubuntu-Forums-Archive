---
title: "Problems with samba and active directory"
date: 2019-05-13
forum: General Help
---

### Post by adubs on 2019-05-13
I have an ubuntu server setup that was working to auth users via AD on 16.04. I have since updated to 18.04 and somewhere along the way no one can authenticate to the share anymore


testparm output:


```
Processing section "[printers]"
Processing section "[X Drive]"
Loaded services file OK.
idmap range not specified for domain '*'
ERROR: Invalid idmap range for domain *!


Server role: ROLE_DOMAIN_MEMBER


Press enter to see a dump of your service definitions


# Global parameters
[global]
        dns proxy = No
        domain master = No
        local master = No
        log file = /var/log/samba/log.%m
        map to guest = Bad User
        max log size = 1000
        obey pam restrictions = Yes
        pam password change = Yes
        panic action = /usr/share/samba/panic-action %d
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        passwd program = /usr/bin/passwd %u
        preferred master = No
        realm = MWSC.MODWHOLESALE.COM
        restrict anonymous = 2
        security = ADS
        server role = member server
        server string = %h server (Samba, Ubuntu)
        unix password sync = Yes
        usershare allow guests = Yes
        winbind enum groups = Yes
        winbind enum users = Yes
        winbind offline logon = Yes
        winbind refresh tickets = Yes
        winbind use default domain = Yes
        workgroup = MWSC
        idmap config example:range = 10000-9999
        idmap config * : backend = tdb
        map acl inherit = Yes
        store dos attributes = Yes
        vfs objects = acl_xattr




[printers]
        browseable = No
        comment = All Printers
        create mask = 0700
        path = /var/spool/samba
        printable = Yes




[X Drive]
        access based share enum = Yes
        comment = Storage Drive
        create mask = 0755
        inherit permissions = Yes
        path = /storage
        read only = No
        valid users = "@MWSC\Domain Users"
        write list = "@MWSC\Domain Users"
```


wbinfo -u outputs a valid AD user list
wbinfo -g outputs a valid AD group list


I also have a nextcloud server and users have no issue logging in with their windows creds so the server clearly can auth correctly, its just samba that doesnt seem to work.


when I do smbclient -L localhost -U [my AD user] I get:


```
tree connect failed: NT_STATUS_ACCESS_DENIED
```


if I fail to enter my password correctly it gives me:


```
session setup failed: NT_STATUS_LOGON_FAILURE
```


so it seems that passwords are working and its just a permissions issue on the share.


Permissions for the dir are ```
drwxrwxrwx+   1 root root  416 May 13 08:42 storage

```

I'm not sure where to go or what to do from here. Any ideas?

---

