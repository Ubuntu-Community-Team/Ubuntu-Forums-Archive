---
title: "Problems extracting archive"
date: 2008-06-13
forum: General Help
---

### Post by codeking on 2008-06-13
I'm trying to extract a archive into a folder protected by the system.  (/etc/fonts/)  Using the terminal (with sudo) returns an error, and the default archive manager returns the following error:

> tar: [filename]: Cannot open: Permission denied

I think its pretty obvious that the archive manager doesn't have permission to write to that directory, but how do I allow it to?

---

### Post by miss.magenta on 2008-06-13
using sudo tar -xzvf <filename> gives you that error?

---

### Post by codeking on 2008-06-13
no the archive manager.  the terminal gives me a different error, something about entry points.... :confused:

---

### Post by robertchahine on 2008-06-13
simply you can extract the archive anywhere, then type 
```
 gksudo nautilus 
```
this open nautilus in root mode, so you can cut (or move) the files extracted to /etc/font without any problem

---

### Post by emichan on 2008-06-13
You can also install fonts into your /home/username/.fonts folder. :)

---

