---
title: "copy to root owned directory"
date: 2007-08-28
forum: General Help
---

### Post by celticbhoy on 2007-08-28
I realise that I must sound like a pillok, but I want to copy the contents of a directory to another directory wich is owned by root. I have tried using 'sudo', but it only copies the files and wont touch the sub-directories. I know this is very trivial, but how do I get the sub-directories to copy!!

---

### Post by strabes on 2007-08-28
Use the -R flag like this:```
sudo cp -R /source/directory /destination/directory
```

"R" stands for "recursive"

The same thing applies to chmodding and chowning files.

---

