---
title: "Permissions denied to mounted network share"
date: 2013-01-20
forum: General Help
---

### Post by cditty on 2013-01-20
I have a network drive that I am able to mount on bootup.  But for some reason, I cannot write to it.  Every attempt gives me permission denied.  

Before it mounts, the directory has cditty.cditty ownership.  Afterwards, it has cditty.root ownership.  I've tried sudo changing the permissions or ownership only to get a permissions denied error again.  

Below is my fstab
```
//192.168.1.71/Shows    /home/cditty/shows/TV2  cifs    guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0       0
```

I'm stuck.  Any ideas?

---

