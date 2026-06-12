---
title: "Samba"
date: 2007-02-19
forum: General Help
---

### Post by WazZzabi on 2007-02-19
All greetings! I from Russia. 
At me such problem. I on work have put ubuntu, and at it is absent samba. At attempt to update packages that samba has appeared, the proxy does not want logining on isa a server. 

Prompt something. 
Thanks!

Used search, has found a heap of decisions but nothing has turned out  :(

---

### Post by anaconda on 2007-02-19
have you already installed samba & smbfs?
if not type this in terminal:
```
sudo apt-get install samba smbc smbfs
```

then you should be able to see & access also samba networks in Places>Network 

I think samba is also included in the ubuntu CD.. it just isn't installed by default. 

(Sorry, if I didn't understand your question correctly..)

---

### Post by WazZzabi on 2007-02-19
In turn I apologize for the English 
on inquiry :
man smb.conf  opens to me a config samba, but correcting it all the same nothing turns out. 
it is impossible to understand samba at me it was established or not :)

---

### Post by WazZzabi on 2007-02-20
Has a little bit understood. 
I have configuration files samba, but itself samba is absent. 
To update I try through a command sudo apt-get update. 
And whether it is possible to execute updating from a local file? To register up to it a way...

---

