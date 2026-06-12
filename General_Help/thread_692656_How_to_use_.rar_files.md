---
title: "How to use .rar files?"
date: 2008-02-10
forum: General Help
---

### Post by ogwilson on 2008-02-10
Is there a program for linux that handles this? preferably one with a gui?

---

### Post by yabbadabbadont on 2008-02-10
Install the unrar (or maybe it is called unrar-nonfree) package and possibly the rar package too.  Then file-roller should be able to open them for you.  However, if they are password protected, then you'll have to use unrar in a terminal window.

```
unrar x myfile.rar
```

---

### Post by yabbadabbadont on 2008-02-10
There is a help topic on this subject that might be of interest to you:

[https://help.ubuntu.com/community/FileCompression?highlight=%28unrar%29](https://help.ubuntu.com/community/FileCompression?highlight=%28unrar%29)

---

### Post by Rhubarb on 2008-02-10
```
sudo aptitude install p7zip-full p7zip-rar
```
This will enable you to open up rar files (and many more other archive formats) with file-roller, so no other applications are required to open / create rar archives.

---

