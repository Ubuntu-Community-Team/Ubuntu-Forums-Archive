---
title: "Samba - Cannot copy files"
date: 2005-04-02
forum: General Help
---

### Post by ola on 2005-04-02
Hi

I'm having problems with Samba on Hoary. It works when I read files but when I try to create files I get this error messages (from windows):'

```

Cannot copy testfile.avi: The specified network name is no longer available.

```

Here is my /etc/samba/smb.conf (I have tried with the original ones as well). 

```

[global]
workgroup = oma
server string = oscar
hosts allow = 127. 192.168.0.
load printers = no
log file = /var/log/samba/log.%m
max log size = 50
security = user
encrypt passwords = true
socket options = TCP_NODELAY
local master = yes
os level = 40
domain master = yes
preferred master = yes
domain logons = yes
wins support = yes
dns proxy = yes
unix charset = iso-8859-1
dos charset = iso-8859-1
display charset = iso8859-1
unix charset = iso8859-1
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
passdb backend = tdbsam guest

[home]
path = /home
public = yes
writeable = yes
printable = no
create mask = 0644
directory mask = 0755
force group = users

```

When I run smbstatus after filewrite that was not successful i get the following. I'm not sure if this is any clue?

```

Locked files:
Pid    DenyMode   Access      R/W        Oplock           Name
--------------------------------------------------------------
13306  DENY_WRITE 0x20089     RDONLY     EXCLUSIVE+BATCH  /home/ola/file Tue Apr  5 22:14:11 2005
13306  DENY_ALL   0x30196     WRONLY     EXCLUSIVE+BATCH  /home/ola/file   Tue Apr  5 22:14:11 2005

```

It also seems like the file is written but it's when it should disconnect or something.. 



Thans for any help!

.o

---

### Post by orion_114 on 2005-04-08
Are you trying to copy from your windows machine to your Ubuntu machine or the other way round ?
It seems to me that your file permission settings are incorrect on the machine you are trying to copy to.

---

### Post by ola on 2005-04-11
It doesn't matter if I copy from my Windows machine or from another Linux machine (it's the writing that's the problem, I think).

I have no idea why, Samba has never been a problem for me before.

Any ideas what I should try?

Thanks.

.o

---

### Post by ola on 2005-04-12
I might have found the problem.. I'm not sure, but it seems like other people having problems with firestarter and samba shares..?

I use firestarter (I have set up rules for incoming traffic) on this machine..

Another idea I have is if I have something wrong with my /etc/hosts file or something?

Updated: I have now removed firestarter and done the iptables rules by hand.. and all of a sudden it seems to work, so I guess I have found the problem...

---

