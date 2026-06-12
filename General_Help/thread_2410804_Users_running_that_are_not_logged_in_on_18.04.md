---
title: "Users running that are not logged in on 18.04"
date: 2019-01-21
forum: General Help
---

### Post by robertzito on 2019-01-21
In run user there is another run/user and I am the only one logged in, when I look at run/use I am seeing the below, is this normal?
```

&#10140;  user ls -a
.  ..  1000  119
&#10140;  user 

```

The owner is Gnome Display Manager, and Owner is gdm,

---

### Post by TheFu on 2019-01-21
yes. completely normal.  Every service runs under a different "daemon account" on Unix systems.  Your smartphone works the same way.  If you look in /etc/passwd, you can see the various different accounts.  Whenever you install a new package that runs as a daemon, it is highly likely that another new account will be created.

This is a security thing for all Unix-like systems, including Linux, Debian, and Ubuntu.

---

### Post by robertzito on 2019-01-21
Thanks for taking the time...

---

