---
title: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the p"
date: 2007-01-06
forum: General Help
---

### Post by timbro on 2007-01-06
I am getting this error when trying to add/remove programs

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

i go into terminal and this happens.

> tim@tim2:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
tim@tim2:~$ 

I don't know what im supposed to do.  I have all the boxes checked under user privaledges.

---

### Post by loell on 2007-01-06
just add the "sudo" before dpkg
like

```
sudo dpkg --configure -a
```

you will then be ask , for you sudo password, enter your password. and dpkg will execute

---

### Post by timbro on 2007-01-06
ty it worked.  what does sudo do?

super user ? ?

---

### Post by pebo on 2007-01-06
Read [this]("https://help.ubuntu.com/community/RootSudo")

---

### Post by dufferdev on 2007-01-09
Awesum.

THIS HELPED ME :)

Thanks a LOT !

---

