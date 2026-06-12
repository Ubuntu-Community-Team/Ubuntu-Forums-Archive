---
title: "set permissions on pdf printer generated files?"
date: 2008-05-07
forum: General Help
---

### Post by prshah on 2008-05-07
Hello,

I'm using the PDF printer built-in with Hardy to print documents. The documents are saved to ~/PDF by default.

However, the documents are saved with 600 permissions by default (-rw------- ), which means that if I access the folder through samba, I don't have read access to the files, (ie, I can't open the files themselves, the share opens fine, and I can see the files). I get the error "Access Denied" when trying to open the files.

If I chmod the file to 664 (-rw-rw-r--) I can then access the file fine across samba.

Is there anyway to specify the default permissions only for files in this folder to be 664 (or anything else as suitable)?

Note that directory permissions (ls -ld PDF) are 655 (drwxr-xr-x), but do not seem to carry down to the files within it.

---

### Post by tamoneya on 2008-05-07
```
sudo chmod -R 664 ~/PDF
```
-R makes it recursive.

---

### Post by prshah on 2008-05-07
> **tamoneya said:**
> ```
sudo chmod -R 664 ~/PDF
```
-R makes it recursive.

First, I don't need sudo; the PDF folder is in my home directory and owned by me.

Second, I don't need recursion, the PDF printer does not create subdirectories.

Third, I need the permissions to be set automatically, everytime the PDF printer creates a file, not manually every time (which is what I'm doing now).

Your attempt to help is appreciated, but you need to reread the original post carefully.

---

