---
title: "apt sources problem"
date: 2007-05-25
forum: General Help
---

### Post by daschmidty on 2007-05-25
After months of perfect apt functionality, I now sometimes run into a problem where i can't install multiverse or universe packages. I have traced this to a problem where my /etc/apt/sources.list file gets removed and replaced with a /etc/apt/sources.list.save if I copy the save to  sources.list, everything works again, but i can't figure out what is causing the problem in the first place.

---

### Post by bapoumba on 2007-05-25
Hello,
Hum, do you mean your sources.list gets modified without your own intervention ?
Please paste it in here:
```
cat /etc/apt/sources.list
```

---

### Post by daschmidty on 2007-05-25
I actually just left town so i will post it tomorrow night when i get back, but it's not so much that it gets modified contents-wise, but rather renamed or perhaps deleted alltogether..

---

