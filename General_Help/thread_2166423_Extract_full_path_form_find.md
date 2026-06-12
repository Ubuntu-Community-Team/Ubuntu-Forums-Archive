---
title: "Extract full path form find"
date: 2013-08-09
forum: General Help
---

### Post by mbnoimi on 2013-08-09
Hello,

I don't know how extract full path from find command to be able to uncompress each file it its path instead of current path
```

find . -iname '*.7z' -exec 7z e {} {} \;

```

---

### Post by Vaphell on 2013-08-09
```
while read -rd $'\0' f; do 7z x -o"${f%/*}" "$f"; done < <( find . -iname '*.7z' -print0 )
```

---

### Post by mbnoimi on 2013-08-09
Thanks a lot.

---

