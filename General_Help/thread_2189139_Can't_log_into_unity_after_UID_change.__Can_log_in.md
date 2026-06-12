---
title: "Can't log into unity after UID change.  Can log into console."
date: 2013-11-20
forum: General Help
---

### Post by the_dingman on 2013-11-20
Greetings,

I recently changed a user's UID to 499 to make them not appear at the login screen.  After doing so, I am not able to log in to unity.  I am simply returned to the login screen.  I am able to log in to the console however.

How does changing the UID affect other settings and permission, and what might I need to do to fix this?  I will mention that this is an encrypted-home account.

---

### Post by steeldriver on 2013-11-20
I suspect that because the user's home directory was encrypted, the system was unable to change the UID/GID on the files in their home directory - when logged in as that user at the console, what do

```
ls -ld ~/
```
and
```
ls -l ~/.{ICE,X}authority
```

say? Do they show ownership as the original (numeric) UID of the user?

---

### Post by the_dingman on 2013-11-20
```

ls -ld ~/

dr-x------ 3 user2 user2 4096 Nov 13 16:42 /home/user2

```
```

ls -l ~/.{ICE,X}authority

ls: cannot access /home/user2/.ICEauthority: No such file or directory
ls: cannot access /home/user2/.Xauthority: No such file or directory

```

Update:

Did a chmod 777 on my home directory and no I can log in.  Thank you!

---

