---
title: "NFS share authentication with Ubuntu Active Directory Domain Controller"
date: 2023-11-08
forum: General Help
---

### Post by arbiter472 on 2023-11-08
Good morning, 

I am in the process of setting up a NFS share server and wish access to the shared folders be authenticated by my Ubuntu Active Directory Domain Controller server. I have tried looking for guides and tutorials on this already but only seem to find guides on how to set up one or the other and not the integration. If this is not possible, what can I do do have my server authenticate network shares?

My end goal is to have a shared folders (one for each chosen/selected user) -either specified or part of a defined group, whose account will authenticate them into **their** shared folder. I could manually set up each folder one by one with the necessary permissions but I wish to automate this as much as possible and considering I have an AD DC on my network with the accounts setup it is my hope that my server can do most of the leg work of the authentication and permissions. 

I will admit I am relatively new to this so any and all guidance will be greatly appreciated. 
Have a blessed day. 
Joe

---

### Post by TheFu on 2023-11-08
[https://ubuntu.com/server/docs](https://ubuntu.com/server/docs) is the official documentation. Always - always, start there.
NFS doesn't work like Samba.  It is a server-to-server authentication method, not end-user -to- server authentication, so the way to authenticate is with Kerberos tickets between the servers.  Permissions are handled through normal Unix file permission controls.

[https://ubuntu.com/server/docs/service-nfs](https://ubuntu.com/server/docs/service-nfs) is the specific NFS guide.  There is a section for _NFSv4 with Kerberos_ followed by _NFS client (using kerberos)_.
AD needs to be setup with POSIX extensions for Unix systems, at least that's what I had to do with my openLDAP setup.  This is separate from NFS+Kerberos.  Typically SSSD is used if MS-AD gets involved. I know that LDAP and NFS work, but I've never used Kerberos at home so I don't know about that.  As far as NFS is concerned, the normal user/group LDAP lookups configured through PAM are all that's needed, IME.

The Ubuntu Community Guide : [https://help.ubuntu.com/community/NFSv4Howto#NFSv4_with_Kerberos](https://help.ubuntu.com/community/NFSv4Howto#NFSv4_with_Kerberos)

---

### Post by MAFoElffen on 2023-11-08
The group permissions for the groups have to be added to the Windows AD manually: [https://ubuntuforums.org/showthread.php?t=2491374&highlight=nfs+share+sssd+kerberos](https://ubuntuforums.org/showthread.php?t=2491374&highlight=nfs+share+sssd+kerberos) . Look at the link in Post #4

---

