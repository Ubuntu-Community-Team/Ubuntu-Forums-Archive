---
title: "Samba install on  Ubuntu"
date: 2013-03-31
forum: General Help
---

### Post by BXRBuddha on 2013-03-31
Hey All,

Working with Ubuntu, I'm trying to configure Samba for my workgroup using this guide

[https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html)

However I'm having problems editing the the text smb.conf file.
The guide makes no mention of it being a read only file (which it is apparently) , so I'm unsure about how to edit it.

 I tried both the terminal and the gedit methods to no avail. 

Thanks

---

### Post by r.stiltskin on 2013-03-31
From a terminal you can run
sudo gedit

or without the terminal press alt+f2, and then in the dialog window: gksu gedit <enter>

That will prompt for your password and open gedit with administrator privileges.

---

### Post by Jay_E on 2013-03-31
hi there.
the file is normally distributed as read-only.
to change the permissions:
cd to the directory of the file
sudo chmod 666 smb.conf

to verify
ls -al smb.conf 

you can edit now.

to write-protect
chmod 444 smb.conf

have fun.
Jay

---

### Post by Morbius1 on 2013-03-31
*** smb.conf is not a read only file. 

*** It's only read only to you since you are not root. 

*** r.stiltskin has the correct answer:
```
gksu gedit /etc/samba/smb.conf
```

*** BTW, it's not a good idea to go around and chmoding system files to 666. 

*** BTW2: I know it's a Ubuntu Sanctioned HowTo and all but that is a very bad HowTo and the share it creates will break ( write access ) the instant you create another share that requires credentials to gain access because at that point that remote user is no longer "nobody".

---

### Post by Jay_E on 2013-04-01
my apologies.
jay

---

