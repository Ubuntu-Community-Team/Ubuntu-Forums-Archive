---
title: "login as root"
date: 2008-02-23
forum: General Help
---

### Post by eskay_karthik on 2008-02-23
hi.
is there any method to login as root ??? because many files require root permissions to view or edit them .. and though i can access them from the terminal, i wud like to know if i can access and edit them from the gui .
pls help.

eskay

---

### Post by eilu on 2008-02-23
try:
```
$gksudo nautilus
```
it will open a root version of nautilus, you can access your files from there. Be careful you don't accidentally break something though.

---

### Post by lncoll on 2008-02-23
For security reassons root is disabled in Ubuntu, this is good to keep as is.
To execute programs, edit files rtc. as root you can do:
In console:

```
user@host$ sudo vim /etc/passwrd
```

Then enter your password and take acces to the file as root.

In the gui:
[ALT] + [F2] -> gksudo gedit /etc/passwrd

This is the best way to. Look for sudo man page.

ALso you can enable root account from System -> Administration -> Users and Groups, and assigning a password to root. I don't recomend this.

---

### Post by taurus on 2008-02-23
Here is more info about sudo/gksudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

