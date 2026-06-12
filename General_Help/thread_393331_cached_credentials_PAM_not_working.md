---
title: "cached credentials PAM not working"
date: 2007-03-25
forum: General Help
---

### Post by seppo on 2007-03-25
I'm trying to get cached credentials working with my OpenLDAP and pam_ldap setup. I'm using the pam-ccreds module on Feisty with the how to:

[https://help.ubuntu.com/community/PamCcredsHowto](https://help.ubuntu.com/community/PamCcredsHowto)

If the ldap server is available, LDAP authentication works fine. If the LDAP server is unavailable (network disconnected) LDAP accounts can't login. the nss-db is available and users and groups can be retrieved from it, but I get the following error upon login:

```
You have been logged on using cached credentials.

Authentication service cannot retrieve authentication info.
```

After that i get logged out again. My current config:

Current pam configuration:
```
 auth    [success=done default=ignore]   pam_unix.so nullok_secure try_first_pass
auth [authinfo_unavail=ignore success=1 default=2] pam_ldap.so use_first_pass
auth [default=done]  pam_ccreds.so action=validate use_first_pass
auth [default=done]  pam_ccreds.so action=store
auth [default=bad]   pam_ccreds.so action=update
password sufficient pam_ldap.so
password required pam_unix.so nullok obscure min=4  max=8 md5
account sufficient pam_ldap.so
account required pam_unix.so
session required pam_unix.so
session required pam_mkhomedir.so skel=/etc/skel/
session optional  pam_ldap.so
session optional  pam_foreground.so
```

Current nsswitch.conf:
```

passwd:        files ldap [NOTFOUND=return] db
group:        files ldap [NOTFOUND=return] db
shadow:         files ldap [NOTFOUND=return] db
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files
protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
netgroup:       nis
automount:    files ldap

```

---

### Post by sean on 2007-08-17
Cached credentials are also not working with PAM and active directory on Gutsy.

Sean

---

### Post by beasty on 2007-10-29
you should check the page ( [https://help.ubuntu.com/community/PamCcredsHowto](https://help.ubuntu.com/community/PamCcredsHowto) )  again ... i just found a fix for it and it seems to work ... 

hope it'll help you in your quest ... 

kr, 

Jdc

---

### Post by seppo on 2007-10-29
Thanks for your reply. I've got it working a couple of months ago. :)

---

### Post by steamboatsailor on 2008-01-24
Trying to wake up this thread.. 

I'm running a Gutsy server with LDAP working fine. Setting up a Gutsy client to talk with the LDAP server, works fine connected too. I can login with users defined in the LDAP.

Following the instructions in the link above ([PamCcredsHowto]("https://help.ubuntu.com/community/PamCcredsHowto")). No problem when connected to my LDAP-server. But when I stop the LDAP server my client will not accept logins for cached users. In fact the client is a bit slow even when using the local user, I think the client it's waiting for the LDAP-server...

I like to debug thing but in this case I event don't know where to begin... Can someone please give me some hints...

/sailor

---

### Post by steamboatsailor on 2008-02-01
Bump ...

---

