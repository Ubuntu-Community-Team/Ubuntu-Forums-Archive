---
title: "how do you do a full text search of all man pages?"
date: 2006-12-01
forum: General Help
---

### Post by ewaguespack on 2006-12-01
apropos only searches the description...

---

### Post by ebash on 2006-12-01
You can try the program program yelp.

---

### Post by ewaguespack on 2006-12-01
I guess I should have said command-line tool...

---

### Post by lamego on 2006-12-01
How to do it with a simple script:
```
#!/bin/bash
for X in /usr/share/man/man?/*
do
        found=`zcat $X | grep -c "$1"`
        if [ $found -gt 0 ];
        then
                echo ------ Fount at $X
                zcat $X | grep "$1"
        fi
done
```

Save it on something like manfind.sh then just use it with:
```
sh manfind.sh word
```

---

