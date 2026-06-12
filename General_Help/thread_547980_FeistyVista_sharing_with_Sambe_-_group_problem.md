---
title: "Feisty/Vista sharing with Sambe - group problem"
date: 2007-09-10
forum: General Help
---

### Post by bigdave146 on 2007-09-10
Hello

I have set up my smb.conf file as per the howtos.  Security is set to share and the actual share itself has force user and force group as "nobody".

I can see the share from Vista but when i click on it I get an error saying "....not accessible.  Group name not found.  If i run smbstatus it says...

Samba version 3.0.24
PID     Username      Group         Machine                        
-------------------------------------------------------------------
 5715   druddle       druddle       vmware       (192.168.1.64)

Service      pid     machine       Connected at
-------------------------------------------------------
IPC$         5715   vmware        Mon Sep 10 23:20:22 2007

No locked files

It shows above that the user druddle is coming in as group druddle too, which is correct when I check the user status on Feisty.  Is the problem that Vista is expecting a different group, or that samba is set up incorrectly.  This is doing my head in now !!!!

](*,)

Dave

---

### Post by bigdave146 on 2007-09-10
Relevant section from smb.conf...

```
[Azureus_Downloads]
    comment = Download_Folder
    path = /home/druddle/Azureus_Downloads
    read only = no
    create mask = 0777
    directory mask = 0777
    force user = nobody
    force group = nobody
    case sensitive = yes
    fstype = Samba
available = yes
browsable = yes
public = yes
writable = yes
```

---

### Post by bigdave146 on 2007-09-11
Anyone ?

---

