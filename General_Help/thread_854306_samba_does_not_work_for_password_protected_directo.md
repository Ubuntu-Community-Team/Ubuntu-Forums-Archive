---
title: "samba does not work for password protected directories"
date: 2008-07-09
forum: General Help
---

### Post by db9s on 2008-07-09
Here's the story, I've got a couple of samba shares running. Some of them have username and passwords attached. But some don't. But I can't manage to browse the protected samba shares even after entering the password on a remote machine.

This problem started happening pretty recently. I do enter the password correctly, but it keeps saying that the contents could not be displayed. 

To make this more confusing is that shares created through Nautilus's GUI work fine, but not any configured through smb.conf. Folders shared through Nautilus's GUI does not appear in smb.conf :confused: What configuration file is samba using them?


Here is my /etc/samba/smb.conf file (I can't browse any of the folders in it):
```


[SHARED_FOLDER]
path = /home/user/SHARED_FOLDER
comment = linux's stuff
available = yes
browsable = yes
public = yes
writable = no

[FirefoxDownloads]
path = /home/user/Documents/FirefoxDownloads
available = yes
browsable = yes
public = yes
writable = no

[linuxBF]
path = /home/user/bitFinished
available = yes
browsable = yes
public = no
writable = yes
valid users = username
create mask = 0644
directory mask = 0755
force user = username
force group = username

[linuxBU]
path = /home/user/Desktop/toburn
read only = no
guest ok = no
valid users = username
create mask = 0600
directory mask = 0700
force user = username
force group = username
available = no
browsable = yes
public = no
writable = no

[linuxUNF]
path = /home/user/bitUnfinished
available = yes
browsable = yes
public = no
writable = yes
valid users = username
create mask = 0664
directory mask = 0755
force user = username
force group = username

```

---

### Post by nikgare on 2008-07-09
Re: Nautilus shares - where are they listed?

/var/lib/samba/usershares/

---

