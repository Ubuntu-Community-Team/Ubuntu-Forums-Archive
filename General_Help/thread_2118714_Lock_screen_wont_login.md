---
title: "Lock screen wont login"
date: 2013-02-22
forum: General Help
---

### Post by wwcaseyss on 2013-02-22
I have recently installed Ubuntu 12.10 and I am using cinnamon as my desktop environment. Today I was trying to setup MTP for my Galaxy nexus and I accidently moved the etc folder off the root to my home folder. In order to fix this I had to boot off the installation disk and move it back off the mounted drive. 

Over the past few hours I have been testing tom make sure everything still works and so far it has with one exception. When I lock the screen (not sign out) it wont accept my password.

Things I have tried include:
-Changing my password
-Making a new user and trying from there
-Disabling password required for login
-Deleting the gnome2 keyring and recreating it.


I am open to suggestions. I would really like to fix this annoyance.



EDIT 2/24/13: I solved this by Re installing off the Installation disc. It is too bad I couldn't just repair it. Thank you

---

### Post by fdrake on 2013-02-22
```
ls -al /etc/passwd /etc/shadow /etc/sudoers
```

you are able to login normally with your password?

---

### Post by wwcaseyss on 2013-02-22
Yes I can login normally and do everything else (termal logins, Promt logins etc.)

```

william@william-desktop:~$ ls -al /etc/passwd /etc/shadow /etc/sudoers
-rw-r--r-- 1 root root 1735 Feb 21 21:57 /etc/passwd
-rw-r----- 1 root root 1069 Feb 21 21:57 /etc/shadow
-r--r----- 1 root root  745 Feb 21 18:51 /etc/sudoers

```


Still looking for a solution. Does anyone know what handles screen locks? is it gnome2?
At this point I would even be willing to reinstall if I got to keep my data.

---

