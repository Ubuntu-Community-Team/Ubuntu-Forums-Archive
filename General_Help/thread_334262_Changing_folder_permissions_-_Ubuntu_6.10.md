---
title: "Changing folder permissions - Ubuntu 6.10"
date: 2007-01-08
forum: General Help
---

### Post by Frankly3D on 2007-01-08
ack Again.

With a ubuntu client have the following automounted folders in fstab.

//server/store00(01)   /mnt/store00(01)  cifs credentials=/root/.cred

all works ok.

But if I try to save something from the  web, I can't as  /mnt/store00(010 )
were created using "sudo mkdir"

I even tried using a launcher with "gksudo nautilus" but still can't change permissions.

would "chmod u+s /mnt/store00(01)" be the way to go?

Frank

---

### Post by Efwis on 2007-01-08
try this
```
sudo chmod 777 /mnt/store00(01)
```
this should give read/write/execute to all users

---

### Post by Frankly3D on 2007-01-09
> **Efwis said:**
> try this
```
sudo chmod 777 /mnt/store00(01)
```
this should give read/write/execute to all users


Hasn't changed the problem.
Only way I can save from web at the moment is with a new launcher

gksudo firefox %u 

But I'd prefer not to keep using it.


Frank

---

