---
title: "[SAMBA] invisible symlink do not display guest account"
date: 2018-03-17
forum: General Help
---

### Post by mickael3 on 2018-03-17
Hello everyone,

I need help for configure my NAS samba share, I want to have access to a share without account. But I have a problem with symbolic links.
The access is readonly, here is the config of the share:
```

[Media]
path = /srv/dev-disk-by-label-DATA/media
guest ok = yes
guest only = yes
read only = yes
browseable = yes
inherit acls = no
inherit permissions = no
ea support = no
store dos attributes = no
vfs objects =
printable = no
create mask = 0664
force create mode = 0664
directory mask = 0775
force directory mode = 0775
hide special files = yes
follow symlinks = yes
hide dot files = yes

```

The symlinks do not appear in this share.
I done a chmod 777 -R to /srv/dev-disk-by-label-DATA/media
and to /srv/dev-disk-by-label-ARCH/media (the dest dir of symlinks


Here is another share accesssible with xxx user, symlinks works perfectly.
```
[Data]
path = /srv/dev-disk-by-label-DATA
guest ok = no
read only = no
browseable = yes
inherit acls = no
inherit permissions = no
ea support = no
store dos attributes = no
vfs objects =
printable = no
create mask = 0664
force create mode = 0664
directory mask = 0775
force directory mode = 0775
hide special files = yes
follow symlinks = yes
hide dot files = yes
valid users = "xxx"
invalid users =
read list =

```
Here is my global config:
```
[global]
workgroup = WORKGROUP
server string = %h server
dns proxy = no
log level = 0
syslog = 0
log file = /var/log/samba/log.%m
max log size = 1000
syslog only = yes
panic action = /usr/share/samba/panic-action %d
encrypt passwords = true
passdb backend = tdbsam
obey pam restrictions = no
unix password sync = no
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes
socket options = TCP_NODELAY IPTOS_LOWDELAY
guest account = nobody
load printers = no
disable spoolss = yes
printing = bsd
printcap name = /dev/null
unix extensions = no
wide links = yes
create mask = 0777
directory mask = 0777
map to guest = Bad User
use sendfile = yes
aio read size = 16384
aio write size = 16384
null passwords = no
local master = yes
time server = no
wins support = no



```

Anybody have ideas of what cause to not display a+rwx symlinks and files please?
Thanks you per advance

---

### Post by TheFu on 2018-03-17
Don't know, but these would be my minimal settings:```

  follow symlinks = yes
  wide links = yes
  guest ok = yes
```

There are serious security considerations in doing this according to the Samba guides.  Best to review those to be certain you are good with the issues.

---

