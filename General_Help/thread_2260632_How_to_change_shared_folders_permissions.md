---
title: "How to change shared folders permissions"
date: 2015-01-13
forum: General Help
---

### Post by tierwalkglide on 2015-01-13
I'm using Lubuntu 14.10 and Windows 7 and they are connected to each other with Samba. In Windows i can see Linux machine and Shared folder. I can also add files to the folder and remove them. But on Lubuntu i can see Shared folder and read it but i can't change permissions on it. I also can't copy anything to that folder or make for example, a new directory. 
 The permissions are: Show content - Anyone, 
                                Change content- Only the owner,
                                 Use content - Anyone
Owner and group are both root.

[Shared]
path = /home/redshift/Shared
guest ok = yes
available = yes
valid users = redshift
read only = no
browseable = yes
public = yes
writable = yes

---

### Post by tierwalkglide on 2015-01-13
sudo chmod -R ugo+rw /home/redshift/Shared

---

