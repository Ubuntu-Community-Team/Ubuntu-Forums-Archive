---
title: "Renaming files #1-30"
date: 2006-10-23
forum: General Help
---

### Post by Jordan Meeter on 2006-10-23
Via the terminal, how can I rename all the files in a directory to one through thirty *.jpg*? For example, 1.jpg, 2.jpg, 3.jpg, etc.

PS, the files are in home/jordan/photos/Lackawanna Railroad/pro/ so would I just use that as the path?

---

### Post by andiii on 2006-10-23
Maybe there are better ways, but it should work with this script:

```
#!/bin/bash
let k=0
for j in $*
do
let k=k+1
mv $j $k.jpg
done
exit 0
```


put this in a file:


$ gedit /tmp/jpgrenamer
*PASTE*
$ chmod a+x /tmp/jpegrenamer
run the script:
$ /tmp/jpegrenamer /folder/with/pictures/*.jpg
$ ls /folder/with/pictures/


make a backup copy of the content of the folder in case something goes wrong :)

---

