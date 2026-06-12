---
title: "SAMBA Security one AD group read/write , all other read only"
date: 2021-05-04
forum: General Help
---

### Post by brianchernish on 2021-05-04
I am trying to add a Samba share to an existing Samba server which is using AD groups for security. I tried following some "Google Results" but can not seem to get it to work.

My working share is defined in smb.conf as:
[IT]
    comment = IT Domain Admins
    path = /sharing/it/
    valid users = @"CLASS4MRO.LAN\Domain Admins"
    force group = "users"
    writable = yes
    read only = no
    force create mode = 0660
    create mask = 0777
    directory mask = 0777
    force directory mode = 0770
    access based share enum = yes
    hide unreadable = yes

I would like the same group ("CLASS4MRO.LAN\Domain Admins") to have read/write rights and all other AD users to have read only access.  Heere is what I tried:
[TechPubs]
        comment = TechPubs
        path = /sharing/it/TechPubs/
        guest = OK
        writable = yes
        read only = yes
            force create mode = 0660
    create mask = 0777
    directory mask = 0777
    force directory mode = 0770
    access based share enum = yes
        force user = root

I am pretty sure I have apples and oranges mixed up. Any insight would be greatly appreciated.

My OS is: Ubuntu 18.04.3 LTS
Thank you.

Brian

---

### Post by rsteinmetz70112 on 2021-05-04
Why do you need another share? Anyone with access to the first share [IT] should be able to access the [TechPubs] directory in it.
Why not duplicate the settings for the first share?

Also "writable = yes" and "read only = yes" seem mutually exclusive. The man page for smb.conf says this > read only 
An inverted synonym is writeable.
They both do the same thing from different directions "writable = yes" is the same as "read only = no".
Also "force user = root" and "force directory mode = 0770" will make sub-directories unreadable by most users, except force "group = "users""  in the parent may override that.

---

