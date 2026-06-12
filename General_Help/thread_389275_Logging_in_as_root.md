---
title: "Logging in as root"
date: 2007-03-20
forum: General Help
---

### Post by cbrain on 2007-03-20
Hello,

Could you please tell me how to to login as the root user because when I do it from the Log in screen I get the message "The system administrator is not allowed to login from this screen".

Thanks.

---

### Post by 23meg on 2007-03-20
You don't have to log in as root. Use sudo instead.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by aysiu on 2007-03-20
Or, if you prefer the point-and-click method, read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by cbrain on 2007-03-20
You've got the wrong idea of why I want to log in as root. Theres something I'm doing in terminal, but it sais there is an error and if I want to fix it I have to run a certain terminal command. When I run this command, it sais I need superuser acces, so I thought I would be able to do it from root.

---

### Post by 23meg on 2007-03-20
Put "sudo" as a prefix to that command. When prompted for a password, enter your user password.

What exactly is the error?

---

### Post by aysiu on 2007-03-20
> **cbrain said:**
> You've got the wrong idea of why I want to log in as root. Theres something I'm doing in terminal, but it sais there is an error and if I want to fix it I have to run a certain terminal command. When I run this command, it sais I need superuser acces, so I thought I would be able to do it from root.
What's the command you're running? *sudo* should take care of it for you.

For example, if you would ordinarily log in as root to move a file to a system folder... ```
su
password:
mv /home/cbrain/file /opt/
``` You would just change the command to *sudo* and forget *su* altogether ```
sudo mv /home/cbrain/file /opt/
password:
``` If you're still having problems, post exactly what you're trying to do and what command you think will accomplish it... as well as what error that command is giving you.

---

### Post by cbrain on 2007-03-20
I am trying to run dpkg --configure -a.

---

### Post by aysiu on 2007-03-20
> **cbrain said:**
> I am trying to run dpkg --configure -a.
Run this, then: ```
sudo dpkg --configure -a
``` When prompted for a password, enter your user password.

---

