---
title: "How to convert all pdf files to subfolders?"
date: 2019-04-08
forum: General Help
---

### Post by jassbru on 2019-04-08
I use the code below, how to make it also convert the files contained in the subfolders?
```
for f in *.pdf; do pdftotext -layout "$f"; done
```

---

### Post by spjackson on 2019-04-08
Welcome to the forums.
```

find . -name "*.pdf" -exec pdftotext -layout {} \;

```

---

### Post by jassbru on 2019-04-08
Thank you!

---

