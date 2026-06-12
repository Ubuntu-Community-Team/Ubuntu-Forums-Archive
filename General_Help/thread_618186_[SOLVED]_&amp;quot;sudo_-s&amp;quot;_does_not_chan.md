---
title: "[SOLVED] &amp;quot;sudo -s&amp;quot; does not change to root user"
date: 2007-11-20
forum: General Help
---

### Post by floopy79 on 2007-11-20
Hi,

I have a problem with sudo -s : it does not change to root user. I enter my password successfully but it remains with the same user :

```
timon@www2:~$ sudo -s
Password:
timon@www2:~$
```

Any help appreciated...
Thanks

---

### Post by banewman on 2007-11-20
First thing to check is if your user has rights to admin the system.
Open user & groups from the menu and check that. :)

---

### Post by floopy79 on 2007-11-20
> **banewman said:**
> First thing to check is if your user has rights to admin the system.
Open user & groups from the menu and check that. :)

Your are right.
my user timon (initial OS user) belongs no more to any group.
How can I add it again since I don''t have sudo access anymore?

ps : I'm on a 6.06 server

---

### Post by banewman on 2007-11-20
To change the user settings you need admin(root) priveleges.
sudo usermod -g admin user
will give user admins group rights
read    man usermod   in terminal for more options  :)

---

### Post by floopy79 on 2007-11-20
> **banewman said:**
> To change the user settings you need admin(root) priveleges.
sudo usermod -g admin user
will give user admins group rights
read    man usermod   in terminal for more options  :)

How can I do it since I don't have sudo access ?
I think I can't log in as root ?

---

### Post by knutschr on 2007-11-20
Log into Recovery mode and give the command there.
(In Recovery mode you are atomatically root).

---

### Post by floopy79 on 2007-11-20
it worked 
thank you all so much :)

---

