---
title: "Synaptic Package Manager mistake"
date: 2006-12-29
forum: General Help
---

### Post by M8M on 2006-12-29
I think I messed up my synaptic package manager. In my attempt to figure out different ways of downloading Money Dance, I tried adding [http://www.getdeb.net/category.php?id=10&release=Dapper](http://www.getdeb.net/category.php?id=10&release=Dapper) to the "custom" option of repositories and obviously it's not a repository site. Now I can't use the synaptic package manager, b/c of an error in line 56 (which is the site listed above). I don't know how to remove it. Can someone please help me?

Thank you.
M8M

---

### Post by ThrobbingBrain66 on 2006-12-29
Open up a terminal and type
```
gksu gedit /etc/apt/sources.list
```
find that line you added and delete it.

Save it, close it and then (In a terminal again) type
```
 sudo apt-get update
```

That should get you up and running again.

---

### Post by M8M on 2006-12-29
Thank you! Thank you! Thank you! It worked.

---

