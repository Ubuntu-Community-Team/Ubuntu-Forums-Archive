---
title: "Mounting Samba share permisions"
date: 2007-10-14
forum: General Help
---

### Post by RudolfMDLT on 2007-10-14
Hi there,

I have started playing with Apache and now I'm ready to start building my website. To make things easier I mapped the "/var/www" folder to a folder on my machine. The problem is that I cannot write to the folder. Right now all that works is SCP. The samba shares work when I do "smb://10.0.0.50/thefolder" but when it's been mapped I only get read only access.

Samba share on the apache machine:
> [BACKUPDRIVE1]
path = /backupdrive1
guest ok = yes
read only = no
available = yes
browseable = yes
public = yes
writable = yes  

[WebDev]
path = /var/www
guest ok = yes
read only = no
available = yes
browseable = yes
public = yes
writable = yes


My Fstab Config:
> //10.0.0.50/backupdrive1 /networkdrives/        smb     defaults        0       0
//10.0.0.50/WebDev      /webdev         smb     defaults        0       0


Any help will be appreciated!

Thanks,

Rudolf

---

### Post by geirha on 2007-10-14
I'm not too familiar with smb, but I think your fstab entries will mount the shares as the guest user. And the guest user probably don't have write permission on the shares(?)

You could add username and password to the options, defaults,username=foo,password=bar , but it's not a good idea to add the password in clear text in your fstab (since anyone with user access to your system will be able to read it)

Have you considered sshfs? [https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

---

