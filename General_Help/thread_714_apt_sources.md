---
title: "apt sources"
date: 2004-10-15
forum: General Help
---

### Post by mbjbdc on 2004-10-15
how can i get root access to add sources?

---

### Post by triad169 on 2004-10-15
```
sudo nano -w /etc/apt/etc/apt/sources.list

```

Or you can do right in Synaptic:

In Synaptic click on *Setting* menu and go down to *Repositories*.

Triad

---

### Post by HungSquirrel on 2004-10-15
To get root access to do a task or two, use sudo and enter your user account's password.  To get permanent root access, set your root password with *sudo passwd root*, then su to root whenever you need to.  I prefer the latter option because it makes me feel safer and I'm used to it anyway.

---

### Post by cseg on 2004-10-15
sudo su - root

---

