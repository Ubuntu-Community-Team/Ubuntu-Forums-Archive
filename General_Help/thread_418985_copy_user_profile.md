---
title: "copy user profile"
date: 2007-04-22
forum: General Help
---

### Post by jmvidalvia on 2007-04-22
I run ubuntu-server, just text mode
I just created a new user, but have some problems:
1- When opening a console, I don see: usr@machine:~$  , just $ ¿how can I get the standard prompt?
2- I would like the new user to belong to same groups as the first user. Do I have to add them one by one? Can't I copy them all? or copy something like the profile of the first user to the new one?
Many thanks!

---

### Post by jmvidalvia on 2007-04-22
Question 1 solved.

```
$sudo usermod -s /bin/bash user
```

---

