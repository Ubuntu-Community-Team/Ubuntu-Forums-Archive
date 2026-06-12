---
title: "Delete any file type that is not .zip"
date: 2008-05-10
forum: General Help
---

### Post by flashuni on 2008-05-10
Hello,
      I am trying to make a script that deletes any folder / file that is not a .zip file. Any help would be appreciated :KS

Flashuni

---

### Post by bingoUV on 2008-05-10
```

find . -not -name '*.zip' -not -name '.' | xargs rm -rf

```

---

### Post by jespdj on 2008-05-10
Note that bingoUV's solution works recursively: it will delete all non-zip files in the current directory and all subdirectories.

It's dangerous if you run this in the wrong directory!

---

