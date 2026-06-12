---
title: "how to give administrator access to a user account"
date: 2008-03-12
forum: General Help
---

### Post by s.jesudasan on 2008-03-12
how to give administrator access to a user account.

---

### Post by scragar on 2008-03-12
since```
sudo su
``` gives you access to root without using the root password(it uses the sudo password instead), I would have thought that a user with root access could simply skip autorisation:
```
sudo su **username**
```

---

### Post by Mikes80 on 2008-03-12
If you mean give administrator access to a basic account. ie another user.
With your original admin account. The one you created at install.

Main menu > Systems > Administration > Users and groups

Then click on the user you want to 'upgrade'

properties > User privileges tab

Then check the box that says 'Administer system'.

Then click OK.

You're now sharing the power. :)

---

### Post by alexforcefive on 2008-03-12
Semantics are fun!

---

### Post by scragar on 2008-03-12
ooh, just noticed how you could read that your way Mikes80.

thinking about it yours makes more sense than my interpritation...

---

