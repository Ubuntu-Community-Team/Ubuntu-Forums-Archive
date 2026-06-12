---
title: "Update Windows password using samba tools?"
date: 2007-05-08
forum: General Help
---

### Post by tors on 2007-05-08
Hi,

I was wondering if it is possible to update my Windows password using some client that comes with samba?

I can login with my current Windows password using

```
smbclient //HOST/SHARENAME  -U username
```

I will be prompted for my password and I can successfully login

Domain=[DOMAIN] OS=[Windows 5.0] Server=[Windows 2000 LAN Manager]
smb: \> 


The Windows system is set to force password changes once a month and I would like to be able to do this without needing to login on a Windows machine *shivers*

Is this possible?

---

