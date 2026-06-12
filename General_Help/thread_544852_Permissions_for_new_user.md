---
title: "Permissions for new user"
date: 2007-09-06
forum: General Help
---

### Post by Razorsharp on 2007-09-06
Hi Im super-newbish to Ubuntu. I accidentally deleted my main user account and I made a new user but I dont know how to give root/admin permission to that user. Is there a command so I can do that in recovery mode?

---

### Post by yabbadabbadont on 2007-09-06
```
gpasswd -a newusername admin
```
Reboot into normal mode and the user with 'newusername' should now be able to use sudo.

---

### Post by Razorsharp on 2007-09-07
thanks that worked

---

