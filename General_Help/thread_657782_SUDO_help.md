---
title: "SUDO help"
date: 2008-01-03
forum: General Help
---

### Post by ebin on 2008-01-03
I was just wondering if I could set my sudo password to be something different than my user password. I don't mind sharing my account password with certain people, but I do not want to give them sudo access because this compromise my system (obviously). Perhaps the solution is to just NOT give them my account password.

---

### Post by jimrz on 2008-01-03
You could create an account for the person OR create a"guest" account, if you have multiple other users in mind, and simply not give the new account(s) sudo privileges.

---

### Post by p_quarles on 2008-01-03
Not giving people your password probably *is *the best solution. However, if you want to be able to let others access your computer -- without letting them change settings -- it's easy to create a non-administrative account. Using the terminal, it's an easy two step process:
1) Type the following, but replace "username" with the name of the new account:
```
sudo useradd -m *username*
```
2) Again, replace "username" with the new account:
```
sudo passwd *username*
```
You will then be prompted to enter the new user's password twice. 

You'll now have an account that can't use "sudo" to change system settings. :)

---

### Post by sciencewhiz on 2008-01-03
You should create new users for them. Go to system->administration->users & groups and add new users. In the users privilege tab, make sure that "administer the system" is unchecked (and anything else you don't want them to be able to do).

---

### Post by bodhi.zazen on 2008-01-04
you cam do this with the rootpw option, :twisted:

>  If set, sudo will prompt for the root password instead of the password of the invoking user. This flag is off by default.

uso visudo, add rootpw to the "Defaults" line :

> Defaults        !lecture,tty_tickets,!fqdn,rootpw

you first need to set a root PW

```
sudo passwd
```

Then edit /etc/passwd

change the last part of the root line to /bin/false

> [noparse]root:x:0:0:root:/root:/bin/false[/noparse]

Now for a root terminal you need sudo /bin/bash

Note this will likely break the recovery mode.

---

