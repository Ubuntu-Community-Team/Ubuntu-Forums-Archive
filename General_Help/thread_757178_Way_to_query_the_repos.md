---
title: "Way to query the repos?"
date: 2008-04-16
forum: General Help
---

### Post by seeker1458 on 2008-04-16
Is there a way to find package in the repos even if you don't know the exact name.  Example, I want to install package XYZ. The package is listed in the repos as Package X-YZ. How do some of you know exactly what to tell apt-get to call?

---

### Post by eriqjaffe on 2008-04-16
```
sudo apt-get update
sudo apt-cache search YZ
```

You can filter the apt-cache search through grep to narrow it down...

```
sudo apt-cache search YZ | grep X
```

btw, that's the a "pipe", not an L or an I.

---

### Post by seeker1458 on 2008-04-16
perfect, exactly what I was looking for. Thanks.

---

