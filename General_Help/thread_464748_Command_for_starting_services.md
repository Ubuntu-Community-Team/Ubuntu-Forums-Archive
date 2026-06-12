---
title: "Command for starting services"
date: 2007-06-05
forum: General Help
---

### Post by carverj on 2007-06-05
G'day all,
               just wondering how one might start a service in Ubuntu.
For example, in Fedora the command is 
```
service crond start||restart||stop
```

---

### Post by jfinkels on 2007-06-05
> **carverj said:**
> G'day all,
               just wondering how one might start a service in Ubuntu.
For example, in Fedora the command is 
```
service crond start||restart||stop
```

I think they're in /etc/init.d:
```

sudo /etc/init.d/gdm start

```

Though I may be horrifically mistaken.

---

