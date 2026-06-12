---
title: "Help with Samba 4.3.9 - Sharing doesn't work anymore"
date: 2016-09-18
forum: General Help
---

### Post by buscat on 2016-09-18
Hi to all,
on my server with Ubuntu 14.04 Server LTS I have one directory shared with Samba and browseable by another PC (Windows 7 Pro).
After Samba 4.3.9 upgrade, it seems that Samba does'n work anymore.
Here is a portion of my /var/log/syslog output:

 STATUS=daemon failed to start: Samba detected misconfigured 'server role' and exited. Check logs for details, error code 22

and here my smb.conf

[global]
workgroup = WORKGROUP
server string = Samba Server %v
netbios name = ubuntu
#security = user
map to guest = bad user
dns proxy = no

load printers = no
printing = bsd
printcap name = /dev/null
disable spoolss = yes
#============================ Share Definitions ==============================
[Stefano]
path = /home/stefano
browsable =yes
writable = yes
guest ok = no
read only = no

Naturally I have a connection error if I browse that directory from Windows...
What can I do? Please, help me!
Thanks in advance

---

### Post by bab1 on 2016-09-18
> **buscat said:**
> Hi to all,
on my server with Ubuntu 14.04 Server LTS I have one directory shared with Samba and browseable by another PC (Windows 7 Pro).
After Samba 4.3.9 upgrade, it seems that Samba does'n work anymore.
Here is a portion of my /var/log/syslog output:

 STATUS=daemon failed to start: Samba detected misconfigured 'server role' and exited. Check logs for details, error code 22

and here my smb.conf

[global]
workgroup = WORKGROUP
server string = Samba Server %v
netbios name = ubuntu
#security = user
map to guest = bad user
dns proxy = no

load printers = no
printing = bsd
printcap name = /dev/null
disable spoolss = yes
#============================ Share Definitions ==============================
[Stefano]
path = /home/stefano
browsable =yes
writable = yes
guest ok = no
read only = no

Naturally I have a connection error if I browse that directory from Windows...
What can I do? Please, help me!
Thanks in advance
Post the output of```
testparm -s 
```
Please use [CODE] blocks for the text output

---

