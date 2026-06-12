---
title: "samba recycler not working on external drives"
date: 2015-06-26
forum: General Help
---

### Post by logan23 on 2015-06-26
Can't seem to get the samba vfs recycler to work on external drives. it creates all the folders and stuff but doesn't create a file.

The permissions one one of the drives are as follows 0775
the recycle folder is 0777

samba version 4.1.11-Ubuntu
Ubuntu Version 14.04.2 LTS

This is a snip of the config
```

[media]   comment = media
   path = /media
   browseable=yes
   available=yes
   public = no
   writable = yes
   printable = no
   create mask = 0765
   vfs object = recycle 
   recycle: repository = /home/recycle/media
   recycle: touch = Yes 
   recycle: keeptree = yes
   recycle: versions = Yes 



```

I really dont know what you guys need but dont hesatate to ask. Ill provide all info needed.

---

