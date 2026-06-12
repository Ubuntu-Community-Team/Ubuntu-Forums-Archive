---
title: "Samba Question"
date: 2008-05-30
forum: General Help
---

### Post by fouadk on 2008-05-30
Hi everyone,

The scenario is that we joined an Ubuntu server to a Windows active directory using winbind and the net tool of Samba...
We can log in successfully on the Ubuntu machine using active directory users.
The problem is we can't log in to the Ubuntu machine from the Windows side using any of the users, including the root of the Ubuntu machine and the Administrator of the Windows server.

Should we create Samba users?

This is a copy of my Samba configuration file
```
[global]
        restrict anonymous = 2
        idmap gid = 10000-20000
        client ntlmv2 auth = yes
        client use spnego = yes
        domain master = no
        encrypt passwords = yes
        winbind use default domain = yes
        realm = OZ.ACC.LAU.EDU.LB
        template shell = /bin/bash
        netbios name = dummy
        writeable = yes
        password server = 172.16.50.11
        idmap uid = 10000-20000
        winbind enum users = yes
        path = /Files
        local master = no
        template homedir = /home/%D/%U
        workgroup = OZ
        winbind enum groups = yes
        winbind refresh tickets = yes
        valid users = root
        security = ads

```

Please help

Thanks in advance

---

