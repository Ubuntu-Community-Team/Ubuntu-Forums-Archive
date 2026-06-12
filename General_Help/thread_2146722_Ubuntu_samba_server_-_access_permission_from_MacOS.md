---
title: "Ubuntu samba server - access permission from MacOS"
date: 2013-05-19
forum: General Help
---

### Post by daniel488 on 2013-05-19
Hi,

I use Ubuntu 13.04 x64. I've installed samba server. My samba settings are default with changes in Global:
```
security = share
```
and in Shares Definitions:
```
[daniel's server]
comment = serwer daniela
read only = no
path = /home/daniel/test2
guest ok = yes
browseable = yes
create mask = 0644
```

I'm trying to cennect from MacOS as a guest. After connecting to smb://192.168.1.100 I see there "daniel's server" volume. But when I'm trying to connect to it there is information "You don't have permission to access". My shared directory has changed permissions with:
```
sudo chmod 0777 /home/daniel/test2
```

I don't know if it is Ubuntu or MacOS side problem, but I'm Ubuntu user so first I'm asking here for help.
Can you tell me if something is wrong with my configuration?

---

### Post by Morbius1 on 2013-05-19
I'm shutting down for the day but you might want to provide more information by posting the output of the following commands:

This one will show us the status of how your system sees smb.conf:
```
testparm -s
```
This one will show us if you are also using Nautilus to share directories:
```
net usershare info --long
```

Without that information it's only speculation at this point:

It could be a conflict with the smb.conf share and the share you created in Nautilus - if you did create one in Nautilus.
It could be that "encrypt passwords = no" instead of yes - and it still has to be yes with guest access.
It could be the /home/daniel doesn't have the right permissions.
It could be that you encrypted your home directory.

If you want to try an experiment change the share definition in smb.conf to this:
> 
[daniel's server] 
comment = serwer daniela 
read only = no 
path = /home/daniel/test2 
guest ok = yes 
browseable = yes
[COLOR=#0000cd]**force user = daniel**[/COLOR] 
create mask = 0644
Then restart samba:
```
sudo service smbd restart
```
The remote guest will be converted to daniel so as long as daniel himself has access so will everyone else.

[COLOR=#0000cd]*Side Note: No one currently living knows exactly how "security = share" works anymore but since this is a guest share I suppose it will work.*[/COLOR]

---

