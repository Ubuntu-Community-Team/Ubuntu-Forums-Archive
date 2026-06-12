---
title: "[SOLVED] deleted home directory"
date: 2008-04-11
forum: General Help
---

### Post by mr_adam on 2008-04-11
Hi
I deleted the only user directory in home. I started a new user account
in the failsafe terminal, and so I have a workable account which has no
sudo priveleges. Is there any way to get them?

---

### Post by ruy_lopez on 2008-04-11
> **mr_adam said:**
> Hi
I deleted the only user directory in home. I started a new user account
in the failsafe terminal, and so I have a workable account which has no
sudo priveleges. Is there any way to get them?

Use the failsafe terminal, and add the new user to the "admin" group. You can do this by adding the username to the /etc/group file. You can add more than one user, seperated by commas.

e.g:
/etc/group
```

...
gdm:x:113:
admin:x:114:newusername1,newusername2
avahi-autoipd:x:115:
...

```

The admin group should be in /etc/group. You don't need to add the group itself. Just add the users to it.

---

### Post by mr_adam on 2008-04-11
Yeah, good call ruy_lopez. That seems to have done the trick. 
Thanks.

---

### Post by harrybazeegar on 2008-04-11
alternatively... you can log into failsafe terminal as root and recreate your home directory...

---

### Post by mr_adam on 2008-04-12
How would you do that? I thought that the whole 
point of sudo was no logging in as root.

---

