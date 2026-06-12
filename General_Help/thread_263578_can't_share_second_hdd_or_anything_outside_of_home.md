---
title: "can't share second hdd or anything outside of home folder."
date: 2006-09-23
forum: General Help
---

### Post by onesojourner on 2006-09-23
I have an ntfs drive that I have all my music on that I am trying to share over my network. it is mounted as hdb1 on my ubuntu machine. when I try to share the folder I want shared I get a share unavailbe error message from my other machine. if I go into system>adim>shared folders and try to share the whole drive I get asked for a password. I have it set to public so I don't understand why it asks for a user name and password. if I share anything inside my home folder it works fine, no password. 

here is the section from my smb.conf file

[media]
path = /media/hdb1/media
available = yes
browseable = yes
public = yes
writable = no

and here is sharing the whole drive

[bigdrive]
path = /media/hdb1
comment = media
available = yes
browseable = yes
public = yes
writable = no

and here is sharing the home folder

[home]
path = /home/peter
available = yes
browseable = yes
public = yes
writable = no

---

### Post by ayoli on 2006-09-23
samba ask for username/password because of this line in /etc/samba/smb.conf
```
security = user
```
if you want it public (less security also) change it for:
```
security = share
```

---

