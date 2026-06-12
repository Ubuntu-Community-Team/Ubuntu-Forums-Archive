---
title: "Rar"
date: 2007-10-31
forum: General Help
---

### Post by johnnyw on 2007-10-31
is there any way apart from this one 

> cat file1.rar file2.rar file3.rar > condensed.rar

to make from various rars one file? I need a more automatic method..

thx

---

### Post by taurus on 2007-10-31
Install unrar

```
sudo apt-get update
sudo apt-get install unrar
```
and unpack the first one.  It will unpack the rest for you into a one single file.

```
unrar x filename.rar
```

---

### Post by johnnyw on 2007-10-31
thx mate, will give it a shot

---

### Post by johnnyw on 2007-10-31
is there any way in which I can see ehich are the errors I had when extracting?


thx

---

### Post by Maestro23 on 2007-10-31
> **johnnyw said:**
> is there any way in which I can see ehich are the errors I had when extracting?


thx

I think there's a flag for it.  Do 

> man unrar

---

