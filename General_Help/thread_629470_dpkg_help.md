---
title: "dpkg help"
date: 2007-12-02
forum: General Help
---

### Post by Somenoob on 2007-12-02
```
user@machine:~$ sudo aptitude update
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
user@machine:~$ sudo dpkg --configure -a
Setting up libc6 (2.6.1-1ubuntu9) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Killed
dpkg: subprocess post-installation script returned error exit status 137
```

I don't recall installing anything recently, now what?

---

### Post by Somenoob on 2007-12-02
never mind, it went away by logging out and in again.

nah, it still remains.

---

