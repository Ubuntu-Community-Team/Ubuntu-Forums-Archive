---
title: "Bash Scripting Help"
date: 2007-03-23
forum: General Help
---

### Post by Bakerconspiracy on 2007-03-23
I would like to make a list of things to download but only use wget once... does anyone know the proper syntax with bash script?

(ex: wget {list of things to download} )

Also I would like to remove lines out of a text file that start with certain characters, can anyone help me with that?

---

### Post by yabbadabbadont on 2007-03-23
Put the URLs of the files you want to download in a text file with one on each line.  Then run:
```
wget -i NameOfFileWithUrls
```

I don't have the exact command syntax off the top of my head, but the sed utility will do it.  I would suggest searching with Google for tutorials as sed regular expressions can be quite complex.

---

### Post by Bakerconspiracy on 2007-03-23
Your help is very much appreciated.

---

### Post by Bakerconspiracy on 2007-03-23
sed -e '/#/d' /home/andrew/Desktop/homeworkdaft.sh | sed 's/^/wget /'> homework.sh

---

