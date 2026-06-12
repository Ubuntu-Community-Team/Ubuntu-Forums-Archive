---
title: "Samba File Server Guest/User Access"
date: 2015-03-21
forum: General Help
---

### Post by jake60 on 2015-03-21
I've been setting up a file sharing server for multiple people and would also like guest access (with no password) on the root [global] of the server. This would allow everyone to open the folder in the network but there would be folders with user authenticated access.

The issue I am having is setting the root of the samba server [global] to allow guest access. It always prompts for a password.

Here is my /etc/samba/smb.conf: (note: users/groups and permissions are correctly set within the filesystem)

```
[global]
workgroup = HOMEWGRP
server string = Home Server %v
netbios name = Home
security = user
guest account = nobody
map to guest = bad user
dns proxy = no


[Jake]
path = /home/jake
valid users = @homegroup
guest ok = no
writable = yes
browsable = yes


[Media]
path = /home/media
valid users = @homegroup
guest ok = no
writable = yes
browsable = yes


[mysite.com]
path = /var/www/mysite.com
valid users = @webgroup
guest ok = no
writable = yes
browsable = yes

```

Any ideas?

Thanks,

---

