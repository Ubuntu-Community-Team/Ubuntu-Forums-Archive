---
title: "Synaptic - Repository export ?"
date: 2020-02-09
forum: General Help
---

### Post by oygle on 2020-02-09
Went into Synaptic hoping to be able to export the repository details, to prepare for a re-installation, but no function there to export.

Noticed the file /etc/apt/sources.list , however it doesn't contain any extras that I have added manually.. They seem to be in the path /etc/apt/sources.list.d

Is there a file that has all the repositories in it ?

---

### Post by wildmanne39 on 2020-02-09
*Thread moved to **General Help a more appropriate sub-forum**.*

---

### Post by oygle on 2020-02-09
Some more searching, this seems to work ...

```
grep ^[^#] /etc/apt/sources.list /etc/apt/sources.list.d/*
```

Ref - [https://www.networkworld.com/article/3305810/how-to-list-repositories-on-linux.html](https://www.networkworld.com/article/3305810/how-to-list-repositories-on-linux.html)

---

