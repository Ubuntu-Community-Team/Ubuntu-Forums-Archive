---
title: "Samba authentication with SSSD?"
date: 2016-08-30
forum: General Help
---

### Post by ry4nm1 on 2016-08-30
I have a linux environment where authentication is done via LDAP (openLDAP).  However, the LDAP directory does not support the samba schema nor can I update it.  I have a linux machine (ubuntu 16.04) that is running sssd for authentication (via LDAP).  On this server, I wish to setup a samba server where I can use my LDAP user/passwords without enabling the samba ldap schemas.   I'm thinking this might be accomplished by using a tdbsam for a backend so I can get the samba attributes, but still use ldap, sssd, pam, whatever for authentication.  It seems I could do this by disabling encrypted passwords, but that is not an open.   Any ideas on how to configure this?

---

