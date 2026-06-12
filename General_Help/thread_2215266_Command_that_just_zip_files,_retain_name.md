---
title: "Command that just zip files, retain name"
date: 2014-04-05
forum: General Help
---

### Post by th3one2 on 2014-04-05
I need an command i just want it to zip whats in the folder and keep the  folder name```
    for f in *; do zip -9r "$f.zip" "$f"; done
```    this  command does what i want but it zips the folder with the content

---

### Post by th3one2 on 2014-04-06
found the command its ```
for dir in */; do ( cd "./$dir" && zip -9r  "../${dir%/}.zip" . ); done
```

---

