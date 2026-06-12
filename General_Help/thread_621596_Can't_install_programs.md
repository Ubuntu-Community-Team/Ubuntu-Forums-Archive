---
title: "Can't install programs"
date: 2007-11-23
forum: General Help
---

### Post by gman12 on 2007-11-23
while i was installing limewire my power blew and my comp restarted, and now every time i open Synaptic Package manager i get this message "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

Please someone help me out :)

---

### Post by qamelian on 2007-11-23
> **gman12 said:**
> while i was installing limewire my power blew and my comp restarted, and now every time i open Synaptic Package manager i get this message "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

Please someone help me out :)
You need to open a terminal (Applications > Accessories > Terminal), and at the command prompt, type:
```
sudo dpkg --configure -a
```and press enter. When prompted for your password, enter the password for your own user account.

---

### Post by gman12 on 2007-11-23
thanks :-D

---

