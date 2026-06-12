---
title: "smb.conf changes"
date: 2005-04-10
forum: General Help
---

### Post by dragev on 2005-04-10
i seup my /etc/samba/smb.conf
and i get it working.
but some how these lines is added:
available = no
public = no
writable = no

and guess what it stops working.  :---)

anyone got a bright idea why this is happening ?

my smb.conf
> 
# Global parameters

workgroup = ninjas
netbios name = ubuntu
encrypt passwords = yes

[homes]
browseable = yes
writelist = ninja

[download]
path = /home/nilsnilsen/downloads
browseable = yes
writelist = ninja

[music]
path = /shared/mp3
browseable = yes
writelist = ninja

[everyone]
path = /shared/everyone
browseable = yes

[appz]
path = /shared/appz
browseable = yes
writelist = ninja

[global]
wins support = no


---

### Post by localzuk on 2005-04-10
[QUOTE=dragev]i seup my /etc/samba/smb.conf
and i get it working.
but some how these lines is added:
available = no
public = no
writable = no

and guess what it stops working.  :---)

anyone got a bright idea why this is happening ?

my smb.conf[/QUOTE]
 My guess would be that a application is altering it on startup. So personally, I would try running chattr +i on smb.conf (sets it to be immutable), so that it can't be altered by the app. Then when you wish to alter it run chattr -i to remove it.

---

