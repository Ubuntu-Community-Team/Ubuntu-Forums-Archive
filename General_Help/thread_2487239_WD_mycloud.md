---
title: "WD mycloud"
date: 2023-05-28
forum: General Help
---

### Post by Y^2om&amp;#7sgP on 2023-05-28
Does anyone know how to connect to a WD mycloud using FileZilla?
I've tried internal and external IP address of my mycloud but both fail, with message unable to connect to server.
Tried googling and found a few suggestions, but each fal
Cheers

---

### Post by howefield on 2023-05-28
Are you wedded to Filezilla ?

Too long since I've used FIlezilla to offer any assistance but sshfs allows you to mount the mycloud as if it were a local drive, something like...

```
sshfs root@192.168.1.100:/DataVolume/shares/Hugh/ /home/hugh/Public
```

mounts my mycloud to the Public folder in ~/

---

