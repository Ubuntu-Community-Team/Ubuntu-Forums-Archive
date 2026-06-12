---
title: "Ubuntu 14.04 joined AD domain but will not authenticate users"
date: 2016-11-14
forum: General Help
---

### Post by campermike on 2016-11-14
I have a 14.04 machine that I added to our AD domain using realmd.  I followed this tutorial: [http://funwithlinux.net/2014/04/join-ubuntu-14-04-to-active-directory-domain-using-realmd/](http://funwithlinux.net/2014/04/join-ubuntu-14-04-to-active-directory-domain-using-realmd/)

The machine said it successfully joined the domain;  however, I am unable to run "id *username"* for any AD users, and I can't log in or switch to any active directory users.  It simply seems to be ignoring the active directory environment.  Has anyone seen this, or are there specific log files that would be useful to figure out why it joined the domain but will not authenticate users to it?  Thanks.

---

### Post by nsa-argentum on 2016-11-14
I have not used realmd, I have always used SAMBA (smb and smb-client), are you trying to have a full suite of active directory services, (file permissions, etc...) or just access to share directories and a smb share drive?

---

### Post by campermike on 2016-11-15
realmd uses Samba and sssd from what I understand.  What we want to do is enable login from domain accounts, and also file shares etc.  Right now, the machine claims to have joined the domain, but it does not show any ids from our AD domain.  Using "getent passwd *username*" does not return, and id *username* also doesn't work for domain accounts.

---

