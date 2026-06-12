---
title: "Different password for Sudo"
date: 2007-08-30
forum: General Help
---

### Post by Aphoxema on 2007-08-30
How can I set Sudo to require a different password than my login password? I SSH/VNC to my computer alot from school and I'd hate to have the wrong person looking over my shoulder. Someone can do some damage with my local user name, but not enough for me to worry about.

My other option would be to make a user-only account, but... really, it would be a little silly to not have the option to have a different password for sudo access.

---

### Post by phibit on 2007-08-30
To change the root account password, you can go into User Accounts menu and change it.

I'm not sure if that will affect the password you're prompted for when you run sudo, but it definately changes the password when you try and do:

```
su root
```

---

### Post by reckless2k2 on 2007-08-30
i'm sure some ninja can chime in with some ninja way to do it but sudo is tied to your username/passwd combo. an option is to kill sudo for you and enable root. then you can block root ssh access. login as yourself and then su to do any serious business. i like sudo but i don't use it on machines that are open to the world through any ports. it is much more difficult to figure out the username and passowrd and then have to figure out the root passwd to gain those priviledges. food for thought. might not be what you want.

---

### Post by ddrichardson on 2007-08-30
There is a way, but its slightly convuluted.

You need to add the runaspw option to /etc/sudoers, e.g.```
# Defaults specification
Defaults:username    timestamp_timeout=0, runaspw, passwd_tries=1
```This forces sudo to need the root password rather than the users. So you would need to enable the root account too.

---

