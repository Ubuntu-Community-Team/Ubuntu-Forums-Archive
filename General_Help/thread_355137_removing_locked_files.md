---
title: "removing locked files"
date: 2007-02-06
forum: General Help
---

### Post by Doug11 on 2007-02-06
I have some folders on my desktop that ended up there after a botched attempt at a certain install. They have a lock on them and even when I try through nautilus, I can't remove them. Any suggestions on how i can get rid of them?

---

### Post by taurus on 2007-02-06
What if you run nautilus as root?

```
gksudo nautilus
```
Or you can remove them the old fashion way, with a terminal.

```
sudo rm **filenames**
```

---

### Post by Doug11 on 2007-02-07
> **taurus said:**
> What if you run nautilus as root?

```
gksudo nautilus
```
Or you can remove them the old fashion way, with a terminal.

```
sudo rm **filenames**
```

nautilus as root didnt work,,,the old fashion way did,,,thanks

---

