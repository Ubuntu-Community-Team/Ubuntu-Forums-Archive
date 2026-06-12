---
title: "how can i delete packages temp. files?"
date: 2007-01-29
forum: General Help
---

### Post by bahrain on 2007-01-29
after installing packages from synaptic package manager or update manager, their temp. files still in the hard disk and take some of its size. where are they? and how can i delete them?

---

### Post by aysiu on 2007-01-29
They're in /var/cache/apt/archives, but there's a setting somewhere in Synaptic to not keep the files. I'll get back to you on where that is.

---

### Post by taurus on 2007-01-29
/var/cache/apt/archives

```
sudo aptitude clean
```

---

### Post by bahrain on 2007-01-29
thanks :)

---

### Post by aysiu on 2007-01-29
Found it.

---

### Post by bionnaki on 2007-01-29
sudo apt-get clean

---

