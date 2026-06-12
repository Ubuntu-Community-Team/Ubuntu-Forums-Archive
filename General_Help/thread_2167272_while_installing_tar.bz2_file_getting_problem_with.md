---
title: "while installing tar.bz2 file getting problem with ./configure"
date: 2013-08-13
forum: General Help
---

### Post by Mohanbabu on 2013-08-13
when i am using ./configure cmd in terminal, itis sowing me no such file or directory. how to do install the tar.bz2 file?

---

### Post by Mohanbabu on 2013-08-13
no such file or directory. so show me the way to install tar bz2 file

---

### Post by monkeybrain20122 on 2013-08-13
Yeah what are you trying to install? A tarball is just an archive (like a zip file) it doesn't have to be source codes inside, maybe it is already compiled and you just need to click a .bin file to start, or maybe it has an install script.. or maybe it uses other way to compile (like cmake). There is no way to help you without knowing more info.

There should be a readme file inside, what does it say?

---

### Post by varunendra on 2013-08-13
You need to be in the directory (in terminal) in which you have extracted the files from the tar.bz2 archive.

For example, if the extracted files are in a directory "mohan" on your desktop, you'll have to change to that directory first -
```
cd Desktop/mohan
```
..then run ./configure (if it is indeed a required step) -
```
./configure
```

---

### Post by codemaniac on 2013-08-13
Threads merged and moved to "General Help".

---

