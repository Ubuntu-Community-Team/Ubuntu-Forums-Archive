---
title: "list all files on the system command?"
date: 2007-09-04
forum: General Help
---

### Post by mpgarate on 2007-09-04
is there a way to use the ls command to view all the files on a linux system?

---

### Post by thelocust on 2007-09-04
```
cd /

ls -R
```

But it's not pretty.

---

### Post by thelocust on 2007-09-04
You might have to do it as root if you want to see absolutely everything. Why do ask by the way, just curios.

---

### Post by thelocust on 2007-09-04
```
ls -aRQ
```

a = Shows hiiden files and folders
R = Shows all subdirectories and contents
Q = Puts all filenames in quotes

---

### Post by mpgarate on 2007-09-04
haha the reason? my friends coming over and his favorite thing in linux is seeing me do stuff with the terminal... so if i kick something off that shows a million files and folders running down the screen... extra props :)

---

### Post by SOULRiDER on 2007-09-04
You can also do:

```
sudo updatedb
locate *
```

---

