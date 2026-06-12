---
title: "How To Disable The Sudo Command"
date: 2007-02-04
forum: General Help
---

### Post by voltage on 2007-02-04
Hi, 

Do some body can tell me how to disable the sudo command ??

Thanks
Rg,
Frank Ong

---

### Post by taurus on 2007-02-04
The best and easiest way is to remove that user from groups adm & admin in /etc/group.  Then, he/she can't sudo anymore.

```
sudo nano -w /etc/group
```

---

### Post by voltage on 2007-02-04
> **taurus said:**
> The best and easiest way is to remove that user from groups adm & admin in /etc/group.  Then, he/she can't sudo anymore.

```
sudo nano -w /etc/group
```

hi,

due to the solution that you are show me, if i remove that user from the groups adm & admin in /etc/group. then, he/she still can login to the xwindow ?

---

### Post by taurus on 2007-02-04
Yes.  She/he can log in and run all the programs like normal user can but she/he can't run the system apps.

---

### Post by voltage on 2007-02-04
> **taurus said:**
> Yes.  She/he can log in and run all the programs like normal user can but she/he can't run the system apps.

Thanks.. it's run. Anyway.. do you have any resources or URL more about the user administrative ? Thanks again.

---

### Post by voltage on 2007-02-04
> **taurus said:**
> Yes.  She/he can log in and run all the programs like normal user can but she/he can't run the system apps.

hi taurus,

after I try the command that you are send to me, I found that.. if i need to disable the sudo command, that is the quick and easy way to do it. But how about, if I need to disable to the selected user or disable to all user ?

Thanks.
Rg,
Frank Ong

---

### Post by taurus on 2007-02-04
You mean disable a user so he/she can't log in anymore?  In that case, you just change the login shell from /bin/bash to /bin/false in /etc/passwd.  Then, that person can't log in anymore unless you change it back.

---

### Post by voltage on 2007-02-04
> **taurus said:**
> You mean disable a user so he/she can't log in anymore?  In that case, you just change the login shell from /bin/bash to /bin/false in /etc/passwd.  Then, that person can't log in anymore unless you change it back.

No... I means allow he/she to login. But they enable to run Sudo command...:confused:

---

### Post by taurus on 2007-02-04
Edit /etc/group

```
gksudo gedit /etc/group
```
and make sure that the login name of that user doesn't appear in groups adm (near the top of the file) and admin (near the end of it).

That's all there is to it.

---

### Post by voltage on 2007-02-04
> **taurus said:**
> Edit /etc/group

```
gksudo gedit /etc/group
```
and make sure that the login name of that user doesn't appear in groups adm (near the top of the file) and admin (near the end of it).

That's all there is to it.

ok .. Thanks.. :)

---

### Post by az on 2007-02-04
By default, only the first user created has sudo priviledges.

If you want a user to not have sudo privs, just create a second user on that system and don't let them access the first user.

---

