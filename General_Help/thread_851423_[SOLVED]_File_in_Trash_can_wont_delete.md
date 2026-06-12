---
title: "[SOLVED] File in Trash can wont delete"
date: 2008-07-06
forum: General Help
---

### Post by Cephaus on 2008-07-06
[IMG]http://img503.imageshack.us/img503/6169/superfailqn2.png[/IMG]

It wont delete and I can't take it out

---

### Post by drs305 on 2008-07-06
You can remove it with the following commands (replace *username* with your log-on name):
```
sudo chown -R *username* /media/disk/.Trash-1000_/files
rm -r /media/disk/.Trash-1000/files
```

---

### Post by PGScooter on 2008-07-06
did you try it from the command line logged in as root?
My guess (as a newb) is that it has to do with the folder name.

---

### Post by Cephaus on 2008-07-06
> **drs305 said:**
> You can remove it with the following commands (replace *username* with your log-on name):
```
sudo chown -R *username* /media/disk/.Trash-1000_/files
rm -r /media/disk/.Trash-1000/files
```

Thanks bro:)

---

