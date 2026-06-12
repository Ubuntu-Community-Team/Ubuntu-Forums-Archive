---
title: "Terminal"
date: 2006-07-15
forum: General Help
---

### Post by thunderduck3141 on 2006-07-15
anyone know how to redirect the output from the terminal (like error messages) to a text file?

---

### Post by Ramses de Norre on 2006-07-15
```
command > file.txt
```
will output the standard output (no error messages) to a file file.txt in the current directory;
```
command &> file.txt
```
will include standard error in the file too.

---

### Post by thunderduck3141 on 2006-07-15
thanks

---

### Post by Ramses de Norre on 2006-07-15
Ow I see I forgot ```
command 2> file.txt
``` will redirect only standard error to file.txt.

---

### Post by Third Thoughts on 2006-07-15
Also if you want to append the output to a file instead of overwriting use >> instead of just >

~Andrew S.

---

