---
title: "How To Mount Network Computer"
date: 2007-02-08
forum: General Help
---

### Post by battleroyalex on 2007-02-08
I want to mount a network computers folder to my desktop. How Do I do this?

For example the path is:
smb://smalltop/Linux

---

### Post by battleroyalex on 2007-02-08
anyone?

---

### Post by tronica on 2007-02-08
do you want to mount this computer localy? If so here yah go

> cd /media

> sudo mkdir sharename

> sudo chmod 777 sharename

> sudo mount -t cifs //ipaddress/sharename /media/sharename -o user=username,pass=password

replace sharename with what ever you please, and the ipaddress is of course of the computer you connection to and then the share you connection to

---

