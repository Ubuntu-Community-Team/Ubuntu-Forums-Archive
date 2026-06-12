---
title: "File extension changing and Bitcomet"
date: 2006-12-28
forum: General Help
---

### Post by Sherlock Holmboy on 2006-12-28
I was trying to bring over a partially downloaded set of files from bitcomet over from my windows partition to Ubuntu. Bitcomet adds a ".bc!" extention to partially downloaded files. Is there a script I can run to just remove the .bc! off the end of the file names?:-k

---

### Post by bruenig on 2006-12-28
Assuming all of the files are in the same directory, just do the following in the terminal.
```
cd /path/to/directory
rename 's/.bc!//' *.bc!
```

---

### Post by Sherlock Holmboy on 2006-12-28
Awsome, thanks. :D  BTW does any one know of a good book that has this stuff in it?

---

