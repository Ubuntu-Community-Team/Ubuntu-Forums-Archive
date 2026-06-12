---
title: "SSH Command Keys Do Not Work When Logged in as New User"
date: 2013-08-26
forum: General Help
---

### Post by fobos3 on 2013-08-26
I have a really weird problem. When I log in normally everything works fine. However, if I switch to the new user, which is not in the sudoers file(shouldn't be relevant), all command keys don't work. When I press the up key, for example, it displays ^[[A. Also the terminal always displays a '$' no matter what directory I am in.

I am pretty sure this is not a su problem because I can do sudo su without a problem. If I login directly to the new user, with SSH, I have the same problems.

Any ideas?

---

### Post by bkline on 2013-08-27
I'm going to guess that you've created a user account which has no home directory, and hence no profile settings.  Try dropping the account (assuming it's really new, and it really has no home directory, or anything else you'd lose) and re-creating it with the -m option (which creates the home directory):

$ sudo useradd -m username

---

### Post by steeldriver on 2013-08-27
... or perhaps it's just that the new user's login shell is /bin/sh... both questions will be answered by

```
getent passwd $USER
```

---

