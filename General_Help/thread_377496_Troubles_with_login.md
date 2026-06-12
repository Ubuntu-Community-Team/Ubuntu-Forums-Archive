---
title: "Troubles with login"
date: 2007-03-06
forum: General Help
---

### Post by pietrob71 on 2007-03-06
The usually user that I use can't login. At startup in the login window I insert my login and password, after 2/3 seconds appear another time the login window and ask to me login and password.

-> CTRL-ALT-F1 -> login with my login and password and I can login

I have tried to make a new user with "useradd -m newuser" and after passwd newuser but the problem is always the same.

I have tried to make a text login like root and after STARX; I can login but the desktop doesn't show the tipical menu of administrator with "users administration" etc, but menu like a user without administration permissions.

Thanks in advance

Pietro

---

### Post by zvacet on 2007-03-06
Go to users&groups and find your new user.Open properties to chek what permissions new user have.Unchek box administer system(I´m not using english version but it is something like that).You can automaticly login by doing this
System -> Administration -> Login Window
```
Security Tab -> Enable Automatic Login (Checked)
Now choose a user from the drop-down menu.
```
I recomend you to pick non-root user for everyday work.if you need to be root just swich user.When you are done with root work back to new user by log out.

---

