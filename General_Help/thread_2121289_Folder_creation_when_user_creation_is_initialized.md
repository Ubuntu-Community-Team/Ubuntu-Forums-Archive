---
title: "Folder creation when user creation is initialized"
date: 2013-03-01
forum: General Help
---

### Post by xienixs on 2013-03-01
Like the title says, is it possible for the sake of consistency to create a standardized home folder when a user is created?

Something like:

~/Programs
~/Scripts
~/Data
~/Junk

---

### Post by steeldriver on 2013-03-01
Have a look at the adduser config file and skel directory

```
/etc/adduser.conf
/etc/skel
```

and the adduser manpage

```
man adduser
```

---

