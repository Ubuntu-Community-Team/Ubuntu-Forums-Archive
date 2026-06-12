---
title: "New to Ubuntu and need a little help."
date: 2008-03-30
forum: General Help
---

### Post by TyrastheRogue on 2008-03-30
Okay.. This is probably going to sound really stupid to a lot of you but I accidentally changed the admin account and made it so there is no account with admin abilities except the root account, so I was wondering if there is a way to change another account to admin so I can access users and groups to remedy the problem. Any help will be greatly appreciated.

---

### Post by Michael.Godawski on 2008-03-30
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by TyrastheRogue on 2008-03-30
That didn't help or maybe I'm just not doing something right, anyone care to enlighten me?

---

### Post by davidpbrown on 2008-03-30
try from a terminal..
```
gksudo users-admin
```

---

### Post by TyrastheRogue on 2008-03-31
Tried that, the only thing I can do that makes anything happen is gksudo nautilus but that asks me for a password and no matter what password I put in it never works.

---

### Post by davidpbrown on 2008-03-31
If you've lost your own superuser password or it was still the random default then you likely don't have a way in. My guess is reinstall the minimum set of partitions and make sure to set the password nexttime.

---

