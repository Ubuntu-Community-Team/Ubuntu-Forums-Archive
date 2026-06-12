---
title: "Setup Ubuntu 22.04 as AD 2016 member with windows network shares"
date: 2023-09-22
forum: General Help
---

### Post by bmillikan2 on 2023-09-22
Hello,

I would like advice on how to join my Ubuntu 22.04 computer to a Windows Server 2016 active directory domain.  In addition, I'd like to have some shares available to the domain.  What is the best way to do this?  It seems there are several ways to do (like using winbind and samba) but I have had issues with that approach.

---

### Post by MAFoElffen on 2023-10-07
I do it this way, following the instructions from there, under "Joining an Active Directory" : [https://help.ubuntu.com/community/22.xx/Active_Directory](https://help.ubuntu.com/community/22.xx/Active_Directory)

Basically you set the DNS nameserver to the Windows Domain Controller, install ssd, ldap, and kerberos client. Then join. The AD User has to exist in Windows AD Users and Groups.

RealmD will join the computer to the AD.

Network shares are a bit more tricky. I don't use WinBind. That is old tech. Samba SMB shares work and carry over the AD permission for Users and Groups. 

NFS shares, well... Adding the network share as a resource to the Domain is the easy part of that, compared to... There are some manual things you have to do to get the user and group permissions to work between the two for NFS shares, where it doesn't automatically remap Win/Linux Users and Groups for that, so all Linux Users and Groups have to be manually added to Win AD.

If you go that route, I have a link to the MS Tech Net doc's on how to do that.

---

