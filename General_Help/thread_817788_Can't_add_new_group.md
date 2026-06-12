---
title: "Can't add new group"
date: 2008-06-03
forum: General Help
---

### Post by Bakon Jarser on 2008-06-03
In 'users and groups' I click on manage groups and I can't click on anything except help and close.  Running this from the terminal as sudo gets the same results and this error:

```
:~$ sudo users-admin

** (users-admin:3714): CRITICAL **: Unable to lookup session information for process '3714'

```

I need to add a new group.  What's happening here?

---

### Post by iaculallad on 2008-06-03
What about doing:

```
sudo addgroup group_name
```

---

### Post by Bakon Jarser on 2008-06-03
That worked.  Thanks.  I guess I'll have to learn how to manage groups from the terminal.

---

### Post by iaculallad on 2008-06-04
You're welcome. Knowing your terminal could give you much flexibility :)

---

