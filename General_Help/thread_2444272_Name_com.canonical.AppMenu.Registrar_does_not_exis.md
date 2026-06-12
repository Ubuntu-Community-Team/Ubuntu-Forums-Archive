---
title: "Name com.canonical.AppMenu.Registrar does not exist on the session bus"
date: 2020-05-27
forum: General Help
---

### Post by c_xy on 2020-05-27
Hello,

We are currently running Ubuntu 18.04 LTS with mate as the desktop environment.

Recently we installed a few updates, and noticed the following error when opening one of our gui applications;



```
Name com.canonical.AppMenu.Registrar does not exist on the session bus
```

We never saw this message in the past, and we're wondering what is the root cause? Is it related to anything important? If not, how does one remove it.

Thanks in advance.

c

---

### Post by CatKiller on 2020-05-27
[This](https://en.wikipedia.org/wiki/D-Bus) is what it's talking about.

Your application is requesting a service that isn't being provided by anything. Why that is, I couldn't say.

---

### Post by c_xy on 2020-06-01
Thanks for the feedback. I'll do some further investigation.

---

