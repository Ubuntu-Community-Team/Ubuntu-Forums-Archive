---
title: "Use windows to view my ubuntu server"
date: 2014-12-29
forum: General Help
---

### Post by stevenroyals on 2014-12-29
Hi

Ive installed samba on a ubuntu sever but can't seem to get another pc with windows on it to see the shared files stored on the server. I'm starting to think that the ubuntu pc has the wrong hdd format for windows to view it. When I installed ubuntu I reformatted the hdd to the required format, can't remember what it was called.

Thanks

---

### Post by steeldriver on 2014-12-29
AFAIK the format of the remote system's HDD should not matter when it is accessed via SAMBA

It is much more likely to be a matter of your SAMBA configuration - can you give details of how you set it up? if you followed a particular set of instructions, please provide a link.

---

### Post by stevenroyals on 2014-12-29
Hi
I have spent quit a bit of time trying to work out the issue searching on the internet and so I couldn't pin point one tutorial in particular since I think of nearly tried them all.
Here is my file at the moment. My windows pc recognises a network connection called server but there is nothing inside it and I cannot create a folder inside it.

Thanks

```

[global]


workgroup = WORKGROUP
security = user
log file = /var/log/samba/log.%m

max log size = 1000

syslog = 0

panic action = /usr/share/samba/panic-action %d
server role = standalone server

passdb backend = tdbsam

obey pam restrictions = yes
unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

pam password change = yes

map to guest = bad user
usershare allow guests = yes

#======================= Share Definitions =======================
comment = ubuntu file server share
path = /srv/samba/share
browsable = yes
guest ok = yes
read only = no
create mask = 0755

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
```

---

### Post by Holger_Gehrke on 2014-12-29
> **stevenroyals said:**
> Hi

#======================= Share Definitions =======================
[COLOR=#ff0000] [NAME_YOUR_SHARE_HERE][/COLOR]
comment = ubuntu file server share
path = /srv/samba/share
browsable = yes
guest ok = yes
read only = no
create mask = 0755


You need to start a new section with the name of the share inside '[]'. Otherwise the settings you've given are seen as part of the previous ([global]) block (and discarded, since they make no sense for global server setup)

---

### Post by stevenroyals on 2014-12-29
Thank you very much. It finally works. Putting in share between the brackets did the trick.

---

