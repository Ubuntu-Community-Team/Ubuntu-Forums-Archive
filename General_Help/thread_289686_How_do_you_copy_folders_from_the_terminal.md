---
title: "How do you copy folders from the terminal"
date: 2006-10-31
forum: General Help
---

### Post by theDentist on 2006-10-31
I want to copy directories from the command line but cp only copies files and omits directories and subdirectories, anyone know the command to copy folders?

Peter

---

### Post by RoyArne on 2006-10-31
```
cp -r <folder> <destination>
```

should do the trick. The *-r* stands for recursive.

---

### Post by Rui Pais on 2006-10-31
Or cp -a if you want to copy recursive *and* preserve ownerships and permissions ;)

---

### Post by theDentist on 2006-10-31
Thanks everyone what would I do without you all  :-D 

Peter

---

### Post by matthewstory on 2006-10-31
if you have problems with cp -r use cp -rf which is recursive force copy paste

---

