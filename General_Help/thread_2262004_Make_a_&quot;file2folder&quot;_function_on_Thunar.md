---
title: "Make a &quot;file2folder&quot; function on Thunar"
date: 2015-01-22
forum: General Help
---

### Post by fkervin on 2015-01-22
Hi all,

A little time ago and thanks to the great help of Morbius1 I created a customized actions on thunar menu to share and unshare folders using samba, it's [in this thread]("http://ubuntuforums.org/showthread.php?t=2257136")

Now I would like to implement a new function, the idea is make this action to a folder and that automatically it would be created inside this folder a sub-folder for every contained file, and then each file wold be moved to its folder.

I've found this script:

```

#!/bin/bash
# Written by MKZA from customerhelp.co.za
find . -type f! | while read file;
do
    f=$(basename "$file")
    f1=${f%.*}
    mkdir "$f1"
    mv "$f" "$f1"
done 
```

But I'm not sure how to store it and make it work in the way i'm telling.

Any help?

Regards in advance :)

---

