---
title: "incron runs bash but not to completion"
date: 2013-01-28
forum: General Help
---

### Post by endergrl on 2013-01-28
I have incron doing:
```
/home/user/preso IN_CREATE bash $@/video1.sh $@ $#
```video1.sh code:
```

#!/bin/sh
fName=$(echo $2 |sed 's/.\{4\}$//')
cp $1/$2 $1/newVids/$2

```Originally the .sh file also included the ffmpeg code:

```
ffmpeg -i $1/$2 -b:v 800k -pass 1 -ar 44100 -b:a 64000 -f flv $1/newVids/$fName.f4v
```If I run the .sh file by itself(with or without ffmpeg code), it works fine.  However, incron runs it it starts to copy the file, but never finishes.  Anyone know what I am doing wrong?

---

