---
title: "wget - download multiple links"
date: 2007-05-28
forum: General Help
---

### Post by wie6Ein0 on 2007-05-28
How can I use wget to download multiple files, one at a time? It needs to download the first file, then when it's completed, start the second file and so on...

Also, is there a way to make wget assign names to each file (renaming)?

---

### Post by endersshadow on 2007-05-28
Don't know about the rename, but you can just make a list of files in the wget command:

```
wget http://file1.com/address http://file2.com/address etc etc
```

---

### Post by toorima on 2007-05-28
wget -r -l1 --no-parent *.* url  will download all files in the dir you specify.

---

