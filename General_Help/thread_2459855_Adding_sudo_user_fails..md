---
title: "Adding sudo user fails."
date: 2021-03-27
forum: General Help
---

### Post by rsteinmetz70112 on 2021-03-27
Ubuntu 20.04 LTS Samba AD-DC
I have added a Linux only user to the computer using standard Linux tools like ```
adduser
``` and set a password using ```
passwd
```

I want to give this user sudo powers. 

I first edited /etc/group to include the new user in the adm and sudo group. That didn't work.
I next tried ```
usermod -aG sudo username
```

/etc/group has the user in both the adm and sudo groups.

When I try to sudo with the user I am prompted for the password but get this error that the ```
user is not in the is not in the sudoers file.  This incident will be reported.
```

I looked a /etc/sudoers and it seems that the adm and sudo group options are commented out.
Yet a user I added earlier and is in the groups does have sudo.

---

### Post by TheFu on 2021-03-27
did  logout/login again?

---

### Post by rsteinmetz70112 on 2021-03-29
Starting a new ssh session didn't work. I could not sudo in the second session.
I redid the steps above and opened another new session and now it works.

---

### Post by TheFu on 2021-03-29
Anytime the sudoers file is modified, the daemon must be restarted.

---

