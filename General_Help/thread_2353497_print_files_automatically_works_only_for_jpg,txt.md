---
title: "print files automatically works only for jpg,txt"
date: 2017-02-22
forum: General Help
---

### Post by amerkamer on 2017-02-22
Hi , i  want to print all files located or uploaded to my folder automatically , the problem is when i drop pdf,docs into this folder printing is failed , i don't know why 
but i am able to print only jpeg,txt 
the code is below : 

```
#!/bin/sh


MONITORDIR="/home/lawrence/Desktop/lawrence/"
inotifywait -m -r -e create --format '%w%f' "${MONITORDIR}" | while read NEWFILE
do
         /usr/bin/lpr "${NEWFILE}"
         rm "${NEWFILE}"
done
```

thanks

---

### Post by HermanAB on 2017-02-22
Hmm, pdf and ps files should print, doc probably not.

---

