---
title: "samba wont restart"
date: 2007-01-29
forum: General Help
---

### Post by Darth_tater on 2007-01-29
help!

this is the error samba gives me when i try to restart it.

```
 [2007/01/29 17:02:19, 0] nmbd/nmbd.c:terminate(58)
  Got SIGTERM: going down...
[2007/01/29 17:02:26, 1] auth/auth_util.c:make_server_info_sam(876)
  User guest in passdb, but getpwnam() fails!
[2007/01/29 17:02:26, 0] smbd/server.c:main(829)
  ERROR: failed to setup guest info.

```

here is my smb.conf file
```

[global]
netbios name = MultiServ
server string = Karls xfer server
workgroup = LOFTAREA
hosts allow = 127. 192.168.0.
printcap name = /etc/printcap
load printers = no
printing = cups
cups options = raw
guest account = guest
log file = /var/log/samba/samba.log
max log size = 1000
security = user
username level = 8
password level = 8
username map = /etc/samba/smbusers
add user script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M %u
smb passwd file = /etc/samba/smbpasswd
encrypt passwords = yes
unix password sync = Yes
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*UNIX*password* %n\n *ReType*new*UNIX*password* %n\n *passwd:*all*authentication*tokens*updated*successfully*\n
null passwords = no
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
interfaces = 127.0.0.1/8 192.168.2.0/24 
remote browse sync =
remote announce = 
local master = no
os level = 33
domain master = no
preferred master = no
time server = no
domain logons = no
logon drive = \
logon home = \home\karl
logon path = \home\karl
logon script = %G.bat
name resolve order = wins lmhosts bcast
wins support = no
wins server =
wins proxy = no
dns proxy = no
preserve case = no
winbind use default domain = yes
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431
template shell = /dev/null



[Web Files]
path = \home\karl\www
comment = Password Protected, Karls use only
valid users = karl
write list = karl
admin users = karl
read only = no
available = no
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no

```

any ideas???

---

### Post by p!=f on 2007-01-29
Does user guest exist in your system?
Try to replace this line
```

guest account = guest

```
with
```

guest account = nobody

```

---

### Post by Darth_tater on 2007-01-29
> **p!=f said:**
> Does user guest exist in your system?
Try to replace this line
```

guest account = guest

```
with
```

guest account = nobody

```

wow... dont know how i missed that!
samba is restarting fine but none of my networked computers can connect. oh well, ill look more into that 2morrow.  off to bed for me.

---

