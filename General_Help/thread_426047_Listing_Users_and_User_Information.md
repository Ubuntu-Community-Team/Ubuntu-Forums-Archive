---
title: "Listing Users and User Information?"
date: 2007-04-28
forum: General Help
---

### Post by ipsi on 2007-04-28
I'm curious if there is a way to list all user accounts on a system, along with information like the groups they belong to and that sort of thing? I can see that such a thing could be classed as a security risk, but it seems like it could be useful. Just curious.

---

### Post by raja on 2007-04-28
You can just look at /etc/group which lists all groups with the users in each.```
cat /etc/group
```

---

### Post by ipsi on 2007-04-28
Wow. That was really simple. Thanks. :)

---

