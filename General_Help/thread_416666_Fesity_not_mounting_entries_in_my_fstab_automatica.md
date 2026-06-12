---
title: "Fesity not mounting entries in my fstab automatically"
date: 2007-04-21
forum: General Help
---

### Post by speedsix on 2007-04-21
I have 2 entries for nfs4 mounts in my fstab that don't mount on boot anymore but 'sudo mount -a' mounts them with no errors. Any ideas?
```

10.0.0.4:/root /mnt/mythtv nfs4 proto=tcp,port=2049,soft        0       0
10.0.0.4:/myth /mnt/myth nfs4 proto=tcp,port=2049,soft          0       0

```


Thanks

Dom

---

### Post by speedsix on 2007-04-23
Anyone?

---

### Post by speedsix on 2007-04-24
Impatient bump

---

### Post by obrouni on 2007-04-24
I think this is to do with it trying to mount the network mounts before network manager has started up and configured itself. 

I could be wrong however. I am also experiencing this with SMB/CIF shares. If I find a solution I will let you know.

---

### Post by speedsix on 2007-04-24
Thanks. Worked fine in Edgy.

---

### Post by speedsix on 2007-05-02
There's a bug filed on launchpad but no sign of a fix yet

[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/46516](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/46516)

---

### Post by speedsix on 2007-06-27
Still so sign of a fix :(

---

### Post by speedsix on 2007-09-08
Still not fixed, this has been broken for ages, can't believe more aren't having this issue?? :confused:

---

