---
title: "My home folder becomes read only"
date: 2013-06-28
forum: General Help
---

### Post by TheHimself on 2013-06-28
Xubuntu 12.10 on a Lenovo laptop. It's the second time my home folder becomes read only, even though the rest (like /etc and other root folders) are not. The first time I booted into the Puppy linux and ran gparted to do a chack of the the relevant partition but no errors were found. Also when I booted back to Ubuntu it did a disk check at the beginning and found no problems. So is it a bug?

---

### Post by alan9800 on 2013-06-28
you might try this:```
chown -hR $USER:$USER /home
```

---

### Post by Impavidus on 2013-06-28
Do you have your /home on a separate partition? In that case it could be remounted read-only if there is an I/O error. It might indicate a bad disk, even if no errors are reported otherwise. I once had that with a USB stick.

---

### Post by TheHimself on 2013-06-28
@alan9800 I did that but I get "Read only file system" errors.
@Impavidus My /home and the rest of the Ubuntu are on the same partition.

---

### Post by alan9800 on 2013-06-28
> **TheHimself said:**
> @alan9800 I did that but I get "Read only file system" errors.which owner and group are shown if you run```
ll
```:?:

---

### Post by Impavidus on 2013-06-28
You don't want to change ownership of /home. Maybe of /home/yourusername, if that's the problem. But in that case I would expect the error "permission denied", not "read only file system".

---

