---
title: "Password required to open Ubuntu 14 LTS"
date: 2015-06-08
forum: General Help
---

### Post by Daniel_Devor on 2015-06-08
To initiate an Ubuntu session a password is required **despite having set System Settings- user account to automatic login.** When I did a clean install it was set to not require a password for log in; now using the settings menu a password is still required. I do not wish to eliminate all password requirements but only the login password requirement. All help will be appreciated.

---

### Post by TheFu on 2015-06-08
Did you happen to encrypt the HOME?

---

### Post by egeezer on 2015-06-08
Does your
 ```
etc/lightdm/lightdm.conf
```
show autologin enabled?
You might also try:
[http://askubuntu.com/questions/530072/how-to-auto-login-in-xubuntu](http://askubuntu.com/questions/530072/how-to-auto-login-in-xubuntu)

---

### Post by ajgreeny on 2015-06-08
It is only the first login after booting that manages to autologin; if you logout and then wish to login again a password is always needed.

---

