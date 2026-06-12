---
title: "Slow user creation with useradd and large LDAP"
date: 2014-09-06
forum: General Help
---

### Post by Daniel_Iwan on 2014-09-06
Hi

My first post on the forum.
I faced an issue where Unix user creation with useradd -p blabla username can take 10 or more minutes

nsswitch is configured to use compat and winbind and OS is connecting with ActiveDirectory for Samba authentication.
AD is large, about 50k users 
This looks awfully similar to

[https://bugs.launchpad.net/ubuntu/+source/shadow/+bug/120015](https://bugs.launchpad.net/ubuntu/+source/shadow/+bug/120015)

but I'm on Ubuntu 12.04 
Anyone had similar issue? Any way to fix or solve that?

Thanks
Daniel

---

