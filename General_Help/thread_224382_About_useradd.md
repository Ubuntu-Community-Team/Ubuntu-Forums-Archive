---
title: "About useradd"
date: 2006-07-27
forum: General Help
---

### Post by seafever on 2006-07-27
I use the ubuntu6.06 system
  when i use the commend "useradd" to add a user
   the problem is ,there is a default password,what's the password
  help! I am a begginner!
root@heq:/home/heq#useradd aaa
root@heq:/home/heq#su aaa
sh-3.1$ passwd
Changing password for aaa
( current) UNIX password: 

passwd&#65306;Authentication failure
:(

---

### Post by aysiu on 2006-07-27
I don't know why you're logged in as root, but instead of typing ```
su aaa
``` try typing ```
passwd aaa
```

---

### Post by seafever on 2006-07-27
> **aysiu said:**
> I don't know why you're logged in as root, but instead of typing ```
su aaa
``` try typing ```
passwd aaa
```

Thanks a lot 
and this is my first time to this forum,haha
thanks

---

### Post by wangbin on 2006-07-27
whatever the default password is, passwd aaa will reset the password for user aaa (assume you are using root)

---

