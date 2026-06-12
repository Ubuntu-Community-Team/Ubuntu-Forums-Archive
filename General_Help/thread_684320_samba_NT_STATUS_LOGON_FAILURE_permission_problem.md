---
title: "samba NT_STATUS_LOGON_FAILURE permission problem?"
date: 2008-02-01
forum: General Help
---

### Post by icemanxp on 2008-02-01
Hi I've been setting up an new server for my family and one of the first problems I've been
having is setting up user accounts for samba to work with non admin users

When I log into samba via smbclient with my admin username all goes well, but
when I try to logon via a user without admin privileges i get this error 

NT_STATUS_LOGON_FAILURE

And in my log this is printed

[2008/01/31 21:52:35, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2008/01/31 21:52:35, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users

My smb.conf (edited down via testparm)

[global]
        workgroup = LANPARTY
        server string = sshBorealis
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[homes]
        comment = Home Directories
        valid users = %S
        read only = No
        create mask = 0775
        directory mask = 0775
        browseable = No

[Share]
        path = /home/common
        read only = No
        guest ok = Yes

Any ideas? do my users need admin privileges for samba to work?

---

### Post by icemanxp on 2008-02-01
Okay so I have now found a parcial fix however I'm not entirely happy with it.
First was I set each users home folder to have rwxr-xr-x, and then I manually logged into their account and set up the smbpasswd. However im not happy with having other users being able to access individual home folders, any Ideas how to allow samba to access these home folders w/o other privileges?

---

### Post by icemanxp on 2008-02-01
okay found the real problem smbclient -U helps when logging in as a different user

---

### Post by matthewboh on 2008-02-01
I'm having the same problems.  I've taken the barest minimal smb.conf file from the Samba.org site and have been editing it.  It's 

```
[global]
workgroup = Workgroup
netbios name = ubuntu
valid users = @mlb

[share1]
path = /tmp

[share2]
path = /media/samba/doc
comment = Some random files

```

If I try to run smbclient - I get 
```
 smbclient //ubuntu/test -W Workgroup -U mlb
Password: 
Domain=[UBUNTU] OS=[Unix] Server=[Samba 3.0.26a]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME

```

Any hints?

---

