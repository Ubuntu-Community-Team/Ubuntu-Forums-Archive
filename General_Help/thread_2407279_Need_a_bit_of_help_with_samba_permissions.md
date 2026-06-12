---
title: "Need a bit of help with samba permissions"
date: 2018-12-01
forum: General Help
---

### Post by hcker2000 on 2018-12-01
I have a couple problems but the big one is I can create a folder via my samba share but I cant create any subfolders or files inside of it.

I have tracked this down to directories marked drwxrwxr-x work but directories created via the samba share are created as drwxr-xr-x

I have also tried forcing the mode to 2775 and 2777 with no difference in permissions.

Whats the best way to fix this given my current samba conf?

My other question is about getting the share to show up to windows computers under Network. I have checked the workgroup matches. The hostname and the server string as well as netbios name all match up (found mixed results on if this matters or not)

Here is my existing samba conf

```

[global]
workgroup = WORKGROUP
server string = hcker2000t1
netbios name = hcker2000t1
netbios aliases = hcker2000t1
security = user
name resolve order = bcast host lmhosts wins
dns proxy = no
bind interfaces only = yes
min protocol = SMB2
guest account = hcker2000
map to guest = bad user
wins support = yes
local master = yes
preferred master = yes

[misc]
path = /media/hcker2000/Misc
read only = no
browsable = yes
guest ok = yes
guest only = yes
writable = yes
force user = hcker2000
force group = hcker2000
create mask = 0775
directory mask = 0775

```

---

### Post by hcker2000 on 2018-12-04
Turns out samba was not using the config file I thought it was. Fixed that and then I added ```
inherit permissions = yes
``` and that fixed my issue.

---

