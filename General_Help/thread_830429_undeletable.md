---
title: "undeletable?"
date: 2008-06-15
forum: General Help
---

### Post by savsav on 2008-06-15
I have something on my xubuntu 8.04 desktop which I cannot delete.

It's a shell script.

When I right-click on it, the "delete" option is greyed out.

Help , please!

---

### Post by drs305 on 2008-06-15
Change the ownership of the file and then delete it:
```
cd ~/Desktop
sudo chown username scriptname
rm scriptname

```

Alternatively, open nautilus (or your file browser) with sudo and remove that way:
```

gksudo nautilus

```

---

### Post by savsav on 2008-06-15
Thanks!

---

