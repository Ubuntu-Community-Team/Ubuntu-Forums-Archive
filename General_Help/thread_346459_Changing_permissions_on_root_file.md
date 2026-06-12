---
title: "Changing permissions on root file"
date: 2007-01-25
forum: General Help
---

### Post by dustin_wielenga32 on 2007-01-25
I am trying to clear up my /etc/network/interfaces file so that I can get my WPA to work (I hope that's all it takes).  So how do I change the permission so that I can attempt to edit the file in Vi or Nano?

Thanks in advance.

---

### Post by taurus on 2007-01-25
Better not change the permission.  Instead, use sudo

```
sudo vi /etc/network/interfaces
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by meng on 2007-01-25
Or, of course
sudo nano -B /etc/network/interfaces
(the -B switch automatically creates a Backup file)

---

### Post by bodhi.zazen on 2007-01-25
Although I like vim :p and nano :p

Why not ```
gksudo gedit /etc/network/interfaces
```

This will also backup to /etc/network/interfaces~

---

