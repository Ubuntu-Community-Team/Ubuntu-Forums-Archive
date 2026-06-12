---
title: "System mounting network share as root"
date: 2021-08-06
forum: General Help
---

### Post by lsutiger on 2021-08-06
I have 3 systems. One is a file server(Debian), the other two are clients(Ubuntu and Xubuntu 20.04)
In the fstab file I have this line in both clients
```
 //192.168.1.15/share/folder /home/user/folder cifs username=user, password=pass 0 0 

```
Here is the contents of the smb.conf file on the server
```
[share]
Comment = Shared Folder
Path = /media/folder
Browseable = yes
Writeable = yes
only guest = no
create mask = 0777
directory mask = 0777
Public = yes
Gueast = ok

```

The Ubuntu computer is mounting the share as that user with read/write capabilities.
The Xubuntu computer is mounting the share as root and I  can only read.

How do I get the Xubuntu to mount it correctly?

---

### Post by Morbius1 on 2021-08-06
To be honest I'm trying to figure out how the Ubuntu machine isn't doing the same thing as the Xubuntu machine.

This mount:
> //192.168.1.15/share/folder /home/user/folder cifs username=user,password=pass 0 0
Should mount with owner = root with write access and read access to everyone else.

If you want it to mount with the client user's name instead of root as owner you need to add another parameter:
> //192.168.1.15/share/folder /home/user/folder cifs username=user,password=pass,uid=morbius 0 0
[COLOR=#ff0000][I]Change morbius to the client user's user name.

Side Note: Is this a typo:[/I][/COLOR]
> Gueast = ok
Did you mean:
```
guest ok = yes
```

---

### Post by lsutiger on 2021-08-06
That did it! Thanks!
And the typo was a typo here, not there.

---

