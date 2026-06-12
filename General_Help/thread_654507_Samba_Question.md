---
title: "Samba Question?"
date: 2007-12-31
forum: General Help
---

### Post by ameba on 2007-12-31
Is

---

### Post by b0rka7a on 2007-12-31
Why do you need to disable it ?

---

### Post by ameba on 2007-12-31
i

---

### Post by Steve1961 on 2007-12-31
Easiest way to stop unwanted services is:

sudo apt-get install bum

then just run the boot up manager (bum) from system/administration menu and uncheck any services you don't need

---

### Post by b0rka7a on 2007-12-31
I still don't get the idea why do you want to remove samba, but try:
```
sudo apt-get remove smb
```, or
```
sudo apt-get remove smbclient
```

---

### Post by ameba on 2007-12-31
Well

---

