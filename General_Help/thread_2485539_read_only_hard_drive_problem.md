---
title: "read only hard drive problem"
date: 2023-04-01
forum: General Help
---

### Post by jgw on 2023-04-01
I have a read only hard drive.  I did it but do not know how.  I have tried all sorts of things to stop the hard drive but a lot of them need the drive to be mounted.  When Disks tries to mount I get:
error creating mount point '/media/greg/93534305b-3831-4a1e-ac38-52fac40a1d4d':read-only file system (udisks-err-r-quark,0)

I have tried several I have found on the net to no avail.  

Thank you...........

---

### Post by MAFoElffen on 2023-04-01
The directory /media is owned by root.

If the filesystem is ext4, after the mount, do (assuming that 'greg' is your username)
```

sudo chown greg /media/greg

```

---

### Post by jgw on 2023-04-02
Thank you for the reply!

worked fine!

---

### Post by MAFoElffen on 2023-04-02
@jqw --
Glad I could help. 

IF this is resolved, please mark the thread as Solved, so that other Users may find what worked for you. (Thread Tools > Solved)

---

