---
title: "cant su to root.."
date: 2008-05-21
forum: General Help
---

### Post by mangaa on 2008-05-21
problem is that my root passwd is not being saved,
after i change/set it at system/admi../users and groups.

therefore when i su,
enter my recently changed/set passwd 
i get authentication failure.

(i would also like to mention that, once accidently my bin folder moved into
sbin folder. thereby i had to create a new folder 'bin' manually, using live
cd.)

thanks

---

### Post by wirelessmonkey on 2008-05-21
> **mangaa said:**
> problem is that my root passwd is not being saved,
after i change/set it at system/admi../users and groups.

therefore when i su,
enter my recently changed/set passwd 
i get authentication failure.

(i would also like to mention that, once accidently my bin folder moved into
sbin folder. thereby i had to create a new folder 'bin' manually, using live
cd.)

thanks

Try using sudo su
su probably won't work by itself in your situation.

---

### Post by mangaa on 2008-05-22
thanks, 
i'll do with it.

---

### Post by spupy on 2008-05-22
With "su" you kind of "login" as root, using roots password. But that wont work on Ubuntu, since the root account is deactivated for login.

With "sudo" and "sudo su" you just run commands with roots privileges, but you use your own password.

---

